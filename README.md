# roundrobin

[![License](https://img.shields.io/github/license/khulnasoft-lab/roundrobin)](LICENSE.md)
![Go version](https://img.shields.io/github/go-mod/go-version/khulnasoft-lab/roundrobin?filename=go.mod)
[![Release](https://img.shields.io/github/release/khulnasoft-lab/roundrobin)](https://github.com/khulnasoft-lab/roundrobin/releases/)
[![Checks](https://github.com/khulnasoft-lab/roundrobin/actions/workflows/build-test.yml/badge.svg)](https://github.com/khulnasoft-lab/roundrobin/actions/workflows/build-test.yml)
[![GoDoc](https://pkg.go.dev/badge/khulnasoft-lab/roundrobin)](https://pkg.go.dev/github.com/khulnasoft-lab/roundrobin)



A Golang Implementation of RoundRobin Algorithm with configurable rotating strategies.

# Features

- Configurable Rotating Strategies
- Track Stats of Each Item
- Generic Implementation
- Concurrency Safe

## Example

An Example showing usage of roundrobin as a library is specified below:

```go
package main

import (
	"fmt"

	"github.com/khulnasoft-lab/roundrobin"
)

func main() {

	ips := []string{
		"192.168.29.58",
		"192.168.29.1",
		"192.168.29.92",
	}

	// create new roundrobin iterator
	rb, err := roundrobin.New(ips...)
	if err != nil {
		panic(err)
	}

	// rb.Add adds given item to sequence
	rb.Add("192.168.29.86")

	for i := 0; i < 10; i++ {
		// rb.Next returns next item in roundrobin fashion
		val := rb.Next().String()
		fmt.Println(val)
	}

	/*
		Output:
		192.168.29.58
		192.168.29.1
		192.168.29.92
		192.168.29.86
		192.168.29.58
		192.168.29.1
		192.168.29.92
		192.168.29.86
		192.168.29.58
		192.168.29.1
	*/

}

```
For more details refer  [GoDoc](https://pkg.go.dev/github.com/khulnasoft-lab/roundrobin) .

## Acknowledgement

Inspired by `https://github.com/hlts2/round-robin`