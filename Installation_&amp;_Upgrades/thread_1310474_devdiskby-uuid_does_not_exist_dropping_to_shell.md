---
title: "/dev/disk/by-uuid/ does not exist dropping to shell"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by linux_user10 on 2009-11-01
Hi,

I am new to unix, i have a old toshiba satellite laptop and recently upgraded to 9.10. Unfortunately i am running into a problem where root cannot locate my disk.  i read the thread [http://ubuntuforums.org/showthread.php?t=813090](http://ubuntuforums.org/showthread.php?t=813090) which explains the solution but i am unable to run sudo, fdisk, look at my fstab, and edit my menu.lst.

whenever i run sudo i get the response: /bin/sh: sudo: not found

i am currently stuck in initramfs or busybox

Thank you! 

Here is the info i get in busybox
Gave up waiting for root device. Common problems:
- boot args (cat /proc/cmdline)
  - check rootdelay=
  - check root=
- missing modules
ALERT! /dev/disk/by-uuid/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX does not exist. dropping to a shell

---

### Post by falconindy on 2009-11-01
/dev/disk/by-uuid isn't available at boot time. Use UUID=xxxxxx

If that fails, refer to the root by /dev/sdXY

---

### Post by linux_user10 on 2009-11-01
omg thank you for the quick reply! 

sorry what do you mean by use uuid=XXXX or refer to to the root by /dev/sdXY
i tried modifying my uuid but it doesnt work i looked into /dev/disk/by-uuid/ and found my a new drive with a different UUID...

sorry i am really new looking at this stuff. the most ive delt with was modifying my alias/environment. I never really tried messing with anything mroe than that

---

### Post by falconindy on 2009-11-01
If for example, you have the snippet:
```
/dev/disk/by-uuid/d5f05c7e-a100-4b02-9f4d-f3ecfbec3925
```
you'd just replace it with:
```
UUID=d5f05c7e-a100-4b02-9f4d-f3ecfbec3925
```
if that doesn't work, you'll just need to reference the disk by its device file name, e.g. sda1 or just:
```
/dev/sda1
```
Under normal operating conditions, all 3 of these are valid methods of referencing a hard drive in Ubuntu. The UUID methods are preferred because the only thing that will change a UUID is formatting the drive. A device file is never guaranteed to be the same on each boot.

---

### Post by linux_user10 on 2009-11-01
ok i was able to finally mod my menu.lst it doesnt seem i have the same issue is anyone else having this issue after installing 9.10? it was working fine for me for the past couple days before it bombed...

---

### Post by pandam@n on 2009-11-02
The problem is that ubuntu thinks your ubuntu-disk is corrupted.... just check that in Gparted in live-cd 9.10.

---

### Post by MickS on 2009-11-02
That sometimes happens to me when I start up my machine, I have found that simply typing exit is enough to start it booting, so far anyway.


Mick

---

### Post by pandam@n on 2009-11-02
> **MickS said:**
> That sometimes happens to me when I start up my machine, I have found that simply typing exit is enough to start it booting, so far anyway.


Mick
Very interesting!.. do you type exit in the (initramfs)-prompt?

---

### Post by AndreLeComte on 2009-11-08
I have the same issue, although it only occurs when booting the 2.6.31 kernel. I have tried changing my menu.ls file with different methods of referencing my hard drive and I have tried typing 'exit' at the (initramfs)-prompt. Neither of these ideas will allow my system to boot the 2.6.31 kernel. Any solution?

---

### Post by AndreLeComte on 2009-11-09
This basically solved the issue for me:
> **arekku said:**
> [Here](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

Replace your nonworking initrd file with a previous version. For you Andre all you need to do is (just in case you are new)

cd /boot
sudo mv initrd.img-2.6.31-14-generic backup
sudo cp initrd.img-2.6.28-16-generic initrd.img-2.6.31-14-generic

---

