## Golang Connectivity Test

### Change connection in helloworld.go

Current connection is to the local default and likely will not work.
Update in helloworld.go the addr field, and include the port. Also include the password.
```
Addr: redis-14299.c1.asia-northeast1-1.gce.cloud.redislabs.com:14299
Password: "XXXXXX"
```

### Testing Against Cloud Redis Stack
# Server
redis_version:6.2.7
redis_git_sha1:e6f67092
redis_git_dirty:0
redis_build_id:8fef4bdabf34d1aa
redis_mode:standalone
os:Linux 5.10.104-linuxkit aarch64
arch_bits:64
```

#### Redis CLI MONITOR output:

```
➜ redis-cli MONITOR
OK
1689879975.224960 [0 172.17.0.1:59432] "hello" "3"
1689879975.240436 [0 172.17.0.1:59432] "set" "foo" "bar"
1689879975.241899 [0 172.17.0.1:59432] "get" "foo"
```

### Against Redis Cloud

Instance created Redis Stack 7.2.0.

#### Database info:

```
> INFO
# Server
redis_version:7.2.0
redis_git_sha1:00000000
redis_git_dirty:0
redis_build_id:0000000000000000000000000000000000000000
redis_mode:standalone
os:Linux 5.4.0-1044-gcp x86_64
arch_bits:64
```

#### MONITOR output:

```
1689880301.677713 [0 99.113.167.177:56066] "hello" "3" "auth" "(redacted)" "(redacted)"
```

#### Golang exit

```
panic: i/o timeout

goroutine 1 [running]:
main.main()
        /Users/savannah.norem/Desktop/git_projects/go_test/helloworld.go:20 +0x174
exit status 2
```
