---
title: "Hardy - ati catalyst drivers above 8.9 - boot to black screen"
date: 2009-01-20
forum: Hardware
---

### Post by talz13 on 2009-01-20
I'm running hardy, 8.04, and just tried installing the new catalyst 8.12 drivers, after being unable to get 8.10 or 8.11 working over the past few months (I believe 8.10 didn't work, it's been a while...).  I followed the instructions for x64 at:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

but each time I end up at a black screen on reboot.  To recap, I did:
```
$ ./ati-driver-installer-8-12-x86.x86_64.run --buildpkg Ubuntu/hardy
$ sudo dpkg -i xorg-driver-fglrx_8.561-0ubuntu1_amd64.deb fglrx-kernel-source_8.561-0ubuntu1_amd64.deb fglrx-amdcccle_8.561-0ubuntu1_amd64.deb fglrx-modaliases_8.561-0ubuntu1_amd64.deb
```
and rebooted.  It showed the ubuntu loading bar, but once it tries to start X (I'm guessing that's what it's doing at that point), it just goes to a black screen, and I can't switch to a vterm, can't login (it's set for auto-login, and I don't hear the login sounds), and I have to hit the reset button on the pc.

I have seen that this is not necessarily an uncommon problem, but I haven't found a good solution on google yet...

---

