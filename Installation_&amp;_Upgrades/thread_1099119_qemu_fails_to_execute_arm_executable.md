---
title: "qemu fails to execute arm executable"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by ritvars on 2009-03-17
Hi, everyone!

Just successfuly created simple arm executable. Wanted to run it with help of qemu-arm tool.

Installed qemu with apt-get (or synaptic - i dont think it realy matters). So far so good.

But when i tried to execute my app
sudo qemu-arm app
i received "Unable to load interpreter"

When i execute qemu-arm whith no params it says:
[..]
-L path           set the elf interpreter prefix (default=/usr/gnemul/qemu-arm)
[..]

It is interesting, but dir /usr/gnemul/qemu-arm  dont even exists!

So i am wondering what i am doing wrong here... Any help will be appreciated! Please, dont give me a hard time - i complete newbie at linuxes. Thanks!

---

### Post by _christoffer on 2010-03-04
I have the exact same question :-) Luckily I'm one step further; look up page 60 in the book "Pro Linux Embedded Systems", for instance on books.google.com, and follow the instructions there. 

Basically, you need install proper ARM libraries from somewhere. There does not seem to be any pre-built Ubuntu packages, so you need to do that manually. From ARM you can get pre-build disk images with base Linux systems, which incidentally includes ARM versions of  some common system libraries. The steps I took to get it to work are

- Download a filesystem image from [http://www.arm.com/community/software-enablement/linux.php](http://www.arm.com/community/software-enablement/linux.php) (I used the minimal ARMv5T one, filename filesystem_bin_armv5t_min.cramfs)

- Mount the image
```
$ sudo mkdir /mnt/tmp
$ sudo mount -o loop -t cramfs filesystem_bin_armv5t_min.cramfs /mnt/tmp/

```- Copy libraries
```
$ sudo mkdir -p /usr/gnemul/qemu-arm
$ sudo cp -a /mnt/tmp/lib/ /usr/gnemul/qemu-arm

```- Test QEMU by running one of the ARM binaries from the image
```
$ /mnt/tmp/bin/ls
<fails, it's an ARM binary>
$ sudo qemu-arm /mnt/tmp/bin/ls
<works!>

```Unfortunately it's way past my bedtime, so this is as far I've come :-) One glaring problem that needs to be solved for me (since this will be deployed on some dev-servers) is that you should not need super-user privileges to run ARM code. If you make more progress than this please post updates!

Edit: However, if you've succeeded in cross-compiling an ARM binary you probably already have these libraries installed somewhere. If so, you could probably just use the "-L" switch and point to them.

---

### Post by _christoffer on 2010-03-09
Oh my, I just realized this question was more than a year old :)

---

