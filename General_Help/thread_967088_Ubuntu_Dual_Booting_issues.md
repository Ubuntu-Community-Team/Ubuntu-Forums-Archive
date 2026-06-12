---
title: "Ubuntu Dual Booting issues"
date: 2008-11-01
forum: General Help
---

### Post by GSiciliani on 2008-11-01
First off, I am new to linux.

I just downloaded ubuntu 8.10 and wubi

**My Problem**is at the windows dual boot menu.  It lists vista and ubuntu.  I select ubuntu and my computer restarts.  There is a short message in white text but it doesn't stay long enough to catch what it says.

Any help please? =]

---

### Post by GSiciliani on 2008-11-02
I took my video camera to see if i could catch the message.

It says

_

Booting GRLDR...

Warning: Unrecognized partition table for drive 82.  Please rebuild using a Microsoft-Compatible FDISK tool(err=114) Current C/H/S=65535/64/32

Starting cmain()..._

---

### Post by sat_e_llite on 2008-11-02
I have a similar problem, it lists out the unrecognised disk partition thing but Ubuntu boots normally. Sorry for hijacking?

---

### Post by GSiciliani on 2008-11-02
I did a complete shut-down and it booted fine.  But there is still a problem.  It went through setup and when I came back to my computer I tried booting into ubuntu again and got the following msg

Booting 'Ubuntu 8.10, kernel 2.6.27-7-generic'

 Filesystem type is ntfs, partition type 0x07
The current working directory(i.e., the relative path) is /ubuntu disks
    [Linux-bzImage, setup=0x3000, size=0x220cb0]
    [Linux-initrd @ 0x7f767000, 0x808d35 bytes]
Loading, please wait...
Gave up waiting for root device.  Common problems:
 -Boot args (cat /proc/cmdline)
   -check rootdelay= (did the system wait long enough?)
   -check roon= (did the system wait for the right device?)
 -missing modules (cat /proc/modules; Is /dev)
ALERT! /dev/disk/by-uuid/8CA280FFA280EED0 does not exist.  Dropping into a shell!


BusyBox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)



ugh.

---

### Post by sat_e_llite on 2008-11-02
Most likely you have a corrupted ubuntu.disk file. Did you try uninstalling and re-installing Wubi?

---

### Post by ago on 2008-11-03
> **GSiciliani said:**
> I did a complete shut-down and it booted fine.

An incomplete shutdown is simply not an option... ;)

---

