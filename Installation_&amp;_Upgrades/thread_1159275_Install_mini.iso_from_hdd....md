---
title: "Install mini.iso from hdd...?"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by blacksm1th on 2009-05-14
Is it possible to install ubuntu minimal iso - mini.iso from hdd?

---

### Post by coffeecat on 2009-05-14
I wouldn't have thought so. The mini.iso is designed to be burnt to CD so that you can boot into a minimal (it really is tiny) system with networking in order to do a network install. Can you enlarge upon what you're trying to do? Why are you wanting to put the mini.iso on the HD?

---

### Post by sisco311 on 2009-05-14
[uhelp]community/Installation/NetbootInstallFromInternet[/uhelp]

[uhelp]community/Installation[/uhelp]

---

### Post by blacksm1th on 2009-05-14
I want to install mini.iso from hdd because i have troubles with my optical drive. It is possible with regular Ubuntu cd's and i love the speed - 2min install.

EDIT: Thank you both for answers.
In community documentation things are not exactly for mini.iso but i managed to boot with mini image. BUT like in Debian itself i can't get network to work because i have DSL type of connection and normally use ppp packages. So i can't install Debian or Ubuntu minimal from hdd or network because there is no way to start ppp connection.

---

### Post by coffeecat on 2009-05-14
> **blacksm1th said:**
> I want to install mini.iso from hdd because i have troubles with my optical drive. It is possible with regular Ubuntu cd's and i love the speed - 2min install.

OK. I've never done that, but I guess you use the mini.iso the same way as you use the regular iso. However, you're not going to get an install in 2 minutes. :) The mini.iso install has to download everything package by package - about 700MB worth. It's slower than downloading the desktop iso because it has to do it package by package. It took me about an hour with the mini.iso - and that was with a good broadband connection.

---

### Post by blacksm1th on 2009-05-14
I have good connection with one of local Ubuntu repositories - around 5mb/sec so it will be fast enough. There are 2 differences between normal iso and mini hdd installs:
1. there is not "vmlinuz" file in mini.iso - downloaded it from [_here_]("http://gb.archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/") - {fixed :)}
2. grub's menu.lst entry is different
normal is:
```
title		Install Ubuntu
root		(hd0,5)
kernel		/vmlinuz boot=casper iso-scan/filename=/LinuxMint-6.iso
initrd		/initrd.gz
```
mini is:
```
title           installer
root            (hd0,5)
kernel          /vmlinuz root=/dev/ram ramdisk_size=1048576 rw
initrd          /initrd.gz
```

Now i can't get network to work in installer because there are no ppp tools.

---

### Post by coffeecat on 2009-05-14
> **blacksm1th said:**
> 1. there is not "vmlinuz" file in mini.iso - downloaded it from [_here_]("http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/")

Two problems with that link. There's no mini.iso there and that's for Hardy. If you want Jaunty, have a look [here](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/).

---

### Post by sisco311 on 2009-05-14
Download the packages you need.

During the installation you can switch to a virtual terminal (Alt+F2) and install the packages with:
```
dpkg -i /path/to/package.deb
```

Set up the network connection and continue with the installation.(Alt+F1)

Or you can use the alternate iso as a repository. Mount the image in /media/cdrom, then
```
apt-cdrom add
apt-get update 
apt-get install package-name
```  

Another option is a hd install with the alternate iso. 
You can download the kernel and initrd from: [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/")

---

### Post by blacksm1th on 2009-05-14
> **coffeecat said:**
> Two problems with that link. There's no mini.iso there and that's for Hardy. If you want Jaunty, have a look [here](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/).
I made a mistake in url - i use vmlinuz from same as yours link. The link to Hardy is from Ubuntu documentation.  mini.iso is from [_here_]("http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/mini.iso")

> **sisco311 said:**
> ...
It will be "rocket science" for me to know which packages are needed for ppp to work :). I will try with alternate cd.

---

### Post by sisco311 on 2009-05-14
[uhelp]community/ADSLPPPoE[/uhelp]

---

### Post by blacksm1th on 2009-05-15
> **sisco311 said:**
> Another option is a hd install with the alternate iso. 
You can download the kernel and initrd from: [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/hd-media/")
Yes this is the right method :). Thank you very much.

---

