---
title: "Intrepid: Boot problem &quot;Gave up waiting for root device&quot;"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by ExemplarUbuntu on 2009-05-27
Yesterday I was updating our remote hosted server from F to G to H and to I.

All went well up to the upgrade to Intrepid and now it won't boot. All I get is this:

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

nosplash will get rid of one error.
I tried adding root_delay=200 but that had no effect.

There isn't a /dev/disks folder. Should the root device be a uuid ?

```

(initramfs) cat /etc/mdadm/mdadm.conf
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e67ba872:6977e81a:7a1f59c7:3ac8710f
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=c57fc8ef:57752efa:58a2cd86:732c3111

```


I really need to get this server up and running again so any help gratefully received.

Peter

---

### Post by ExemplarUbuntu on 2009-05-27
The support chaps managed to re-install mdadm and get the box to boot up with some alterations to sources.list to use their own dist archive.

---

### Post by ExemplarUbuntu on 2009-05-28
This is bad.

I have just updated our internal server from version H to I and it has done the exact same thing. The only difference is that it is using a uuid for the drive.

I have more control over this machine than the remotely hosted one but how do get mdadm to work ?

UPDATE:
Luckily there are 2 kernels to choose from in grub.

2.6.27-14-generic fails with ALERT! /dev/disk/by-uuid/<long uuid> does not exist. Dropping to a shell!

2.6.24-24 boots ok

Is there a fix for this ?
Has it been fixed in Jaunty ?

---

### Post by AndreLeComte on 2009-11-08
I have the same issue although it only occurs with the 2.6.31 kernel. I can boot Ubuntu 9.10 by using the 2.6.28 kernel. Any solution?

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

