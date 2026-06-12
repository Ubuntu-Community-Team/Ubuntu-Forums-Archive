---
title: "loading alsa driver supporting xifi sound- error"
date: 2009-10-25
forum: Hardware
---

### Post by Chainek on 2009-10-25
Hi.

I've been following these guides to install my xifi soundcard:
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/]("http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/")

[http://wiki.debian.org/X-Fi]("http://wiki.debian.org/X-Fi")

I am at the very last command of the second guide for installing the actual driver and keep getting an error.

I am inputting this:
```
modprobe snd-ctxfi
```
and getting this:
```
bryan@bryan-desktop:~/alsa-driver-1.0.21$ sudo modprobe snd-ctxfi
FATAL: Error inserting snd_ctxfi (/lib/modules/2.6.28-16-generic/updates/alsa/pci/ctxfi/snd-ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

I appreciate any help.

---

