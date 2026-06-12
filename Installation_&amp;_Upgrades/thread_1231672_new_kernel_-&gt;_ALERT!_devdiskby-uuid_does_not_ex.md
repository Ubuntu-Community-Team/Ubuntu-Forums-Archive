---
title: "new kernel -&gt; ALERT! /dev/disk/by-uuid does not exist"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by Fredvs79 on 2009-08-04
So I did a fresh install of Ubuntu 9.04 server on a new computer. There is only 1 sATA hard drive. 
Now I want to install the real-time kernel environment RTAI. ([www.rtai.org](www.rtai.org)).

Steps so far included 
* downloading rtai-3.7.1, which has latest patches for the 2.6.23 kernel.
* downloading the linux-2.6.23 kernel source and unpacking it.
* patching the kernel source with the rtai patch
* configure the kernel options, make the kernel (no errors), create a .deb file with make-kpkg, and install the .deb package of the kernel. I noted however that my menu.lst file was not altered, so I added in the relevant bits for the new kernel image.

I reboot the computer to use the new kernel, and I get the error message:

[I]Gave up waiting for the root device. Common problems:
 - Boot args (cat /proc/cmdline)
    - check root delay
    - check root
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/f4...ccc does not exist. 
Dropping to a shell![/I]

First I rebooted a working kernel and then went back into my /boot/grub/menu.lst file and checked to make sure the uuid was correct. It was. 

Then I tried changing the root delay with the argument rootdelay=130 in the grub options line. No change.

Then I tried adding pci=nomsi in the grub options line. No help.

Then I tried the following commands

[B]ls -l /dev/disk/by-uuid
ls -l /dev/disk/by-id[/B]

and both gave me no such device errors

I tried 
**cat /proc/partitions**
and I discovered there was nothing there
I tried
**cat /etc/fstab**
and there was also nothing there.
I tried
**mnt /dev/sda2 /mnt**
but get no such device errors

I'm at my wits end as to why this is happening. Most of the other people on the web who have this problem experience it when not properly upgrading. They boot the live CD and do a "dist upgrade" or "apt-get update, apt-get upgrade" and fix the problem. It isn't really clear if this is a bug, or why it happens.

Any help is appreciated.

---

### Post by bibil.thaysose on 2010-06-21
I'm having this problem as well with my 2.6.35 kernel.  However, /dev/disk/by-uuid does exist on my filesystem, so maybe it is a different problem.  Have you been able to fix this by recompiling?  I'm wondering if there is some sort of compilation flag that must be set in order to have support for disk by-uuid.  If you have figured this out, please post back.  If not, someone please help us!  :confused:

---

### Post by Mecasickle on 2010-10-04
I'm having the same problem using ubuntu 9.10 using the 2.6.22 kernel and RTAI 3.8

---

### Post by Joe Momma on 2010-10-12
Same issue here, I found a solution here.

[https://bugs.launchpad.net/ubuntu/+bug/659149](https://bugs.launchpad.net/ubuntu/+bug/659149)

It says to add pci=nocrs to your boot command in grub.  Seems more like a workaround to a bug that should be fixed.

---

