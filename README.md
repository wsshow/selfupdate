# selfupdate
单文件程序自动升级库

## 安装
```bash
go get github.com/wsshow/selfupdate
```

## 例子
```golang
import (
    "fmt"
    "net/http"

    "github.com/wsshow/selfupdate"
)

func doUpdate(url string) error {
    resp, err := http.Get(url)
    if err != nil {
        return err
    }
    defer resp.Body.Close()
    err = selfupdate.Apply(resp.Body, selfupdate.Options{})
    if err != nil {
        // error handling
    }
    return err
}
```

## 参考
- https://github.com/minio/selfupdate
- https://github.com/inconshreveable/go-update