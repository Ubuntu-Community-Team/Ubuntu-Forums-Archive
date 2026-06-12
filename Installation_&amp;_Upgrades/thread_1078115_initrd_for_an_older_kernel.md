---
title: "initrd for an older kernel ?"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by rmccabe3701 on 2009-02-23
I am using ubuntu 8.10 and am trying to run an older kernel (2.6.15-5) for some testing purposes.  The problem is that the mkinitramfs setup is not made for the older kernel.  My steps are as follows:
```

make mrproper

```

```

make menuconfig

```

```

make bzImage && make modules && make modules_install && make install

```

The last "make install" will make the initrd, but it does it for the new (2.6.27-11) kernel.  For instance, upon startup, Busybox complains that
```

libata: unknown parameter 'ignore_hpa'

```
It turns out that this module parameter wasn't introduced until around 2.6.20 or so.  I fixed this by mounting the initrd image and commenting out any mention of "ignore_hpa" -- but it still cannot load the root filesystem, because I am not sure if it has all the modules it needs ...

I have been troubleshooting this for several days and am getting nowhere.
My questions are:

-- Is there a simple way make mkinitramfs make the initrd correctly for an older kernel?

-- If not, can I just compile all the modules into my kernel image so that I don't need a initrd?  If I don't use an initrd do I simply leave that line out in the menu.lst?

-- How do I tell which SCSI drivers to compile into the kernel?

Thanks in advance.

---

### Post by rmccabe3701 on 2009-02-25
Any help?

---

### Post by rmccabe3701 on 2009-03-02
bump

---

### Post by ExemplarUbuntu on 2009-05-26
I have spent the day upgrading a remote host from Ubuntu F to G to H to I

The first updates went ok but the update to Intrepid tried to reboot and failed:

```
Couldnt get a file descriptor referring to the console
usplash: libusplash.c:289: switch_console: Assertion `(saved_vt >= 0) && (saved_vt < 10)' failed.
libata: Unknown parameter `ignore_hpa'
libata: Unknown parameter `ignore_hpa'
libata: Unknown parameter `ignore_hpa'
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/md1 does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>
(initramfs)

```

I urgently need to know how to get it to reboot. The libata error looks like a good starting point.

---

### Post by rmccabe3701 on 2009-12-20
Still no reply to this thread?  At work we are trying to compile (a patched version of) the 2.6.21 kernel.  The kernel does not boot (boots into busybox saying it can't find the root device).  The problem is we don't know how to configure this kernel.  Many sites tell you to do 
```
cp -vi /boot/config-`uname -r` .config
```
but this assumes the kernel you are running (2.6.31-15-generic in my case) is the same as the one you are trying to build (2.6.21).  I'm guessing the older kernel cannot load since we don't have this baseline .config file (or don't know how to make menuconfig correctly for our hardware -- dell inspiron 600).  
Has anyone know how to build/boot a ~2.6.21-ish kernel using a 2.6.31-ish system?

---

