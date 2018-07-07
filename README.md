# snowflake
snowflake uuid

## Getting Started

### Installing

This assumes you already have a working Go environment, if not please see
[this page](https://golang.org/doc/install) first.

```sh
go get github.com/zhenorzz/snowflake
```

### Usage

Import the package into your project then construct a new snowflake WorkID using a
unique node number. The default settings permit a node number range from 0 to 1023.
If you have set a custom NodeBits value, you will need to calculate what your
node number range will be. With the node object call the Generate() method to
generate and return a unique snowflake ID.

Keep in mind that each worker you create must have a unique node number, even
across multiple servers.  If you do not keep node numbers unique the generator
cannot guarantee unique IDs across all nodes.

**Example Program:**

```go
package main

import (
	"fmt"

	"github.com/zhenorzz/snowflake"
)

func main() {

    // Create a new Node with a Node number of 1
    sf, err := snowflake.New(1)
    if err != nil {
        panic(err)
    }

    // Generate a snowflake ID.
    uuid := sf.Generate()

    // Print
    fmt.Println(uuid)
}
```
