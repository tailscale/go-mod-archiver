# go-mod-archiver

Afraid of being unable to build historical versions of your Go program?

`go mod vendor` lets you check in your dependencies to git, but that's both bloaty and tedious.

It's nicer to work day-to-day with only `go.mod` (and no `vendor` folder), trusting that
https://proxy.golang.org/ can give you any module version in the future.

Except https://proxy.golang.org/ doesn't necessarily retain everything forever.

Hence this project. **`go-mod-archiver`** is meant to run as a GitHub
Actions workflow and whenever your `go.mod` changes, it runs `go mod
vendor` and commits it into a git tag so you can get your dependent
code in the future if you really need to. (by syncing back to some old
point in time, looking at the SHA-256 of your `go.mod`, and fetching
that tag's `vendor` directory)
