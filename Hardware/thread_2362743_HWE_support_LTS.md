---
title: "HWE support LTS"
date: 2017-06-01
forum: Hardware
---

### Post by paul.a on 2017-06-01
Server Ubuntu 14.04.5 LTS (GNU/Linux 3.19.0-25-generic x86_64) (full apt update and upgrade except distro) showed on reboot:
> WARNING: Security updates for your current Hardware Enablement Stack
ended on 2016-08-04:
 * [http://wiki.ubuntu.com/1404_HWE_EOL](http://wiki.ubuntu.com/1404_HWE_EOL)
but the wiki page shows support until April 2019 with the Xenial 4.4 kernel, so as per wiki:
> sudo apt-get install --install-recommends linux-generic-lts-xenial
Done... but inxi -Fx still showing after reboot:
> System:    Host: server4 Kernel: 3.19.0-25-generic x86_64 (64 bit, gcc: 4.8.2) Console: tty 0 Distro: Ubuntu 14.04 trusty
Any thoughts or suggestions, please
Note: all my other servers are 16.04, but I just need this one for legacy MySQL 5.5 reasons.
Thanks -- paul

---

### Post by #&amp;thj^% on 2017-06-01
* You are affected if it shows a kernel with the following version: 3.16 or 3.19 or 4.2
  * You are not affected if it shows a kernel with the following version: 3.13 or 4.4 

This method does not check for a HWE graphics stack. However, you cannot get a HWE graphics stack without a corresponding HWE kernel unless you've done things manually. Note that such a combination (HWE graphics with non-HWE kernel) is not supported. 

```
hwe-support-status --show-all-unsupported

```

Upgrading the kernel shouldn't change much for you **unless you are using the AMD and fglrx drivers**

So there will be no more updates to the 3.19 kernel as 15.04 is EOL (No longer supported)

So to upgrade the kernel I usually run this:
```
sudo apt-get install linux-image-generic-lts-xenial linux-generic-lts-xenial
```

Or:
```
sudo apt-get install linux-signed-generic-lts-xenial linux-signed-image-generic-lts-xenial
```

---

### Post by paul.a on 2017-06-02
Thank you for replying. I have tried your suggestions, which are variants of what I had already tried, but this server (14.04.5 LTS) still uses "uname -r 3.19.0-25-generic". Maybe I've traced this to grub.

The "upgrade" to a Xenial-based 4.4 kernel does install it to /boot but gives the following:
>  /.../
Replacing config file /run/grub/menu.lst with new version

But the write to grub is failing (ignored, whatever):
> cat: /run/grub/menu.lst: No such file or directory
I'm guessing this is a bug, there is no mention of grub in syslog or boot.log -- on a desktop you might see grub, on a rack-mount server through ssh it's invisible.
Again thanks -- paul

---

