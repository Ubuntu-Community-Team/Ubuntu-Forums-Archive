---
title: "Upgraded to 9.04, on boot dropped to busybox..."
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by kerryhall on 2009-04-26
Upgraded to 9.04

On boot, dropped to busybox.

Got the following errors:

*No block devices found
*Gave up waiting for root device
*Alert! Can't find /dev/mapper/nvidia_cajdbccj2

---

### Post by jim_24601 on 2009-04-27
I have the same problem. It seems that upgrading to 9.04 has a few problems if you have a RAID setup (not, apparently, restricted to nvidia fakeraid, either).

---

### Post by aderyn81 on 2009-04-27
same problem using the fake raid1 of an amd chipset. maybe new kernel does not load mdadmin automatically? help... :(

---

### Post by aderyn81 on 2009-04-27
same problem: [http://ubuntuforums.org/showthread.php?t=1138480](http://ubuntuforums.org/showthread.php?t=1138480)

---

### Post by bsmith1051 on 2009-04-27
Can someone point me to any existing posts/bugs about this problem?  I have 8.10 with software RAID and I'm afraid to upgrade to 9.04 until this gets sorted-out.  Or, is my setup unaffected?

---

### Post by jim_24601 on 2009-04-27
I was able to boot by selecting the 2.6.27-11-generic kernel from the grub menu; it still dropped me into busybox, but I could do
```
dmraid -ay
exit
```
after which it booted quite happily. This didn't work with the default 2.6.28 kernel, though--dmraid complained that the array was already active, and indeed the array appeared in /dev/mapper, but no partitions were visible within it.

---

### Post by foresto on 2009-04-27
Is this bug related?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153)

---

### Post by aderyn81 on 2009-04-27
ok, it worked. :popcorn:

after first boot i did

```
sudo update-grub
```

and started with 2.6.28 kernel, it seems all is working.

thanks to all :)

---

### Post by jim_24601 on 2009-04-30
I got my computer to boot using the 2.6.28.11 kernel, but my solution was a little different. It turns out that the kernel module for my setup (nvidia fakeraid 5) wasn't being loaded at boot. I edited /etc/initramfs-tools/modules and added the line
```
dm_raid4_5
```
then ran
```
sudo update-initramfs -u
```
after which the new kernel boots and runs fine.

---

