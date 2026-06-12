---
title: "ppscsi for kernel 4.2.0"
date: 2016-01-05
forum: Hardware
---

### Post by dc740 on 2016-01-05
I got it to work. Check the latest module modification and instructions here:[https://github.com/dc740/ppscsi](https://github.com/dc740/ppscsi)

Outdated:
I haven't tried this yet, but I got the driver to compile in the latest kernel (Ubuntu 15.10 4.2.0-22-generic ) and also "fixed", or removed all warnings. I'm planing to give it a try later with an old HP 5100C, but even if I don't succeed, this modification may come handy for someone else

Steps
EDIT: now that it works, I also created a repository in github: [https://github.com/dc740/ppscsi](https://github.com/dc740/ppscsi)
```
make
sudo cp ppscsi.ko epst.ko /lib/modules/`uname -r`/kernel/drivers/parport
sudo depmod -a
sudo /bin/sh -c 'echo "SUBSYSTEM==\"scsi_generic\",ATTRS{type}==\"3\", SYMLINK=\"scanner%n\", MODE=\"0777\", GROUP=\"scanner\"" >> /etc/udev/rules.d/45-libsane.rules'
sudo service udev restart
sudo modprobe ppscsi
sudo modprobe epst
```


Good luck!

---

### Post by dc740 on 2016-01-05
Success. I just tried with my very old HP 5100C scanner, and it worked flawlessly.

Notes:
I don't have a parallel port in my main desktop, so I didn't use kernel 4.2.0, I used another machine which was using kernel 3.19 0-28 (Ubuntu too).
The driver compiles in both version, and at least I can confirm it works fine in 3.19. I guess it should also work in 4.2.0.

---

