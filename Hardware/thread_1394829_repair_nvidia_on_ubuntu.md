---
title: "repair nvidia on ubuntu"
date: 2010-01-31
forum: Hardware
---

### Post by revo_bharat@yahoo.co.in on 2010-01-31
i installed nvidia.run correctly on a hcl leaptop.
it was working excellent.
but after a update in ubuntu package manager 
after a restart nvidia server fail to start on system boot up leading to a dull graphics 
i am also not able to reinstall the same nvidia driver as the "IT IS ALREADY INSTALLED"
"visit ftp://nvidia.download.com"
tried a lot 
please help i am new to ubuntu and do not know much .

---

### Post by raffaele181188 on 2010-01-31
I often get in troubles with NVidia .run packages, 'cause they don't get updated when you upgrade your kernel and so.
I'd try removing .run package and installing ubuntu version
```

sudo ./NVIDIA-XXXXXX-pkgN.run --uninstall
sudo apt-get update
sudo apt-get install nvidia-185

```

---

