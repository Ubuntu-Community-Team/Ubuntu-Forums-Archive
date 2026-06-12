---
title: "Compiling from source code"
date: 2010-11-21
forum: Hardware
---

### Post by domagoj412 on 2010-11-21
Hello, I am trying to install driver for this DAQ card:
[http://support.advantech.com/support/DownloadSRDetail.aspx?SR_ID=1-41GHVV&Doc_Source=Download](http://support.advantech.com/support/DownloadSRDetail.aspx?SR_ID=1-41GHVV&Doc_Source=Download)

But when I execute (as in given documentation):
```
insmod /usr/.../advdrv_core.ko
```
as error i get this:
```
invalid module format
```

As I found out this is because downloaded driver is for kernel  2.6.18 so it will not work on new one...

But there is also source code provided so is it posible to copile it for this kernel?

---

