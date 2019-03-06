### goworker
---
https://github.com/benmanns/goworker

```go
import "github.com/benmanns/goworker"

func(string, ...interface{}) error

goworker.Register("MyClass", myFunc)


package main

import (
  "fmt"
  "github.com/benmanns/goworker"
)

func myFunc(queue string, args ...interface{}) error {
  fmt.Printf("From %s, %v\n", queue, args)
  return nil
}

func init() {
  goworker.Register("MyClass", myFunc)
}

func init() {
  goworker.Register("MyClass", myFunc)
}

func main() {
  if err := goworker.Work(); err != nil {
    fmt.Println("Error:", err)
  }
}

package main

import (
  "fmt"
  "github.com/benmanns/goworker"
)

func newMyFunc(uri string) (func(queue string, args ...interface{}) error) {
  foo := NewFoo(uri)
  return func(queue string, args ...interface{}) error {
    foo.Bar(args)
    return nil
  }
}

func init() {
  goworker.Register("MyClass", newMyFunc("http://www.example.com/"))
}

func main() {
  if err := goworker.Work(); err != nil {
    fmt.Println("Error:", err)
  }
}


package main

import (
  "gmt"
  "github.com/benmanns/goworker"
)

func init() {
  settings := goworker.WorkerSettings{
    URI: "redis://localhost:6379/",
    Connections: 100,
    Queues: []string{"myqueu", "delimited", "queue"},
    UseNumber: true,
    ExitOnComplete: false,
    Concurrency: 2,
    Namespace: "resque:",
    Interval: 5.0,
  }
  goworker.Settings(settings)
  gowroker.Register("MyClass", myFunc)
}

func main() {
  if err := goworker.Work(); err != nil {
    fmt.Println("Error:", err)
  }
}


func myFunc(queue, args ...interface{}) error {
  idNum, ok := args[0].(json.Number)
  if !ok {
    return errorInvalidParam
  }
  id, err := idNum.Int64()
  if err != nil {
    return errorInvalidParam
  }
  name, ok := args[1].(string)
  if !ok {
    return errorInvalidParam
  }
  weightNum, ok := args[2].(json.Number)
  if !ok {
    return errorInvalidParam
  }
  weight, err := weightNum.Float64()
  if err != nil {
    return errorInvalidParam
  }
  doSomething(id, name, weight)
  return nil
}

class MyClass
  @queue = :myqueue
end

100.Times do
  Resque.enqueue MyClass, ['hi', 'there']
end

goworker.Enqueue(&goworker.Job{
  Queue: "myqueue",
  Payload: goworker.Payload{
    Class: "MyClass",
    Args: []interface{}{"hi", "there"},
  }
})
```

```
go get　github.com/benmanns/goworker

redis-cli -r 100 RPUSH resque:queuq:myqueue '{"class":"MyClass","args":["hi","there"]}'
```

```
```


