---
title: "Are my headers installed correctly?"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by chrispy212 on 2009-06-27
Hey,
So I have a problem. When I try and use make, or m-a build I get an error about my headers not being installed. However, in /usr/src, I have linux-headers-2.6.27-7-generic, linux-headers-2.6.28-13 and linux-headers-2.6.28-13-generic, with my kernel being 2.6.28-13-generic. I also have a link from /usr/src/linux to linux-headers-2.6.28-13-generic.

```
$ sudo apt-get install linux-headers-$(uname -r)
``` tells me that 0 packages need installing or upgrading.

```

$ cd /lib/modules/$(uname -r)
$ rm -f build source    # They technically shouldn't exist anyway
$ ln -s /usr/src/linux-headers-$(uname -r) build
$ ln -s /usr/src/linux-headers-$(uname -r) source

```
returns no errors, but does not fix the problem

```
$ sudo m-a prepare
```
returns
```

chris@medion-laptop:~$ sudo m-a prepare
[sudo] password for chris: 
Getting source for kernel version: 2.6.28-13-generic
apt-get install linux-headers-2.6.28-13-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.28-13-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Done!

```


I am thoroughly stumped, and this has stopped my use of my new ubuntu install fresh in it's tracks. Any help would be greatly appreciated.

---

