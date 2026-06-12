---
title: "Ubuntu 5.10 raid1 lilo problem help!"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by mslonik on 2006-02-01
Welcome!

I have successfully installed the Ubuntu 5.10 with software raid 1 as discribed on wiki.ubuntu.com - "Installation/LVMOnRaid" ([https://wiki.ubuntu.com/Installation/LVMOnRaid?highlight=%28raid%29)](https://wiki.ubuntu.com/Installation/LVMOnRaid?highlight=%28raid%29)). 

After some time I decided to slightly modify the lilo.conf and run lilo. After that change my system is not longer bootable. When I run Ubuntu from Live! CD and then:
lilo -t
I see the following lines:
[B]Warning: /proc/partitions does not match /dev directory structure
(...)
Fatal: is_primary: Not a valid device 0xFE02[/B]

I should mentione that version of my lilo is:
lilo -V
22.6.1 (Ubuntu)

During the boot I see "Kernel panic" message.

Can anybody help me? Every clue is appreciated, even as simple as redirecting me to the right forum / group...

Kind regards,
mslonik

---

### Post by mslonik on 2006-02-04
Again, what I've been doing since Ubuntu Live! ends its booting process:

$ sudo su
# cd /mnt
# mkdir dev proc boot sys
# mount -v -t ext3 /dev/PV/root /mnt
# mount -v -t ext3 /dev/PV/boot /mnt/boot
# mount -v -t proc none /mnt/proc
# mount -v -t sysfs none /mnt/sys
# mount -v --bind /dev /mnt/dev

# chroot /mnt /bin/bash
# update-initramfs -v -c -k 2.6.12-10-386
# /sbin/lilo

Warning: '/proc/partitions' does not match '/dev' directory structure.
Name change: '/dev/dm-0' -> '/dev/mapper/casper-cow'
Fatal: is_primary: Not a valid device: 0xFE07

So the same problem again :-(
---------------------------------------------------------

My /dev/mapper directory:

+ PV-boot              254,2
+ PV-home             254,5
+ PV-root               254,4
+ PV-swap             254,3
+ PV-zasoby           254,6
+ casper-cow          254,0
+ casper-snapshot   254,1
- control

---------------------------------------------------------

My lilo.conf:

boot = /dev/md0
root = /dev/mapper/PV-root
raid-extra-boot = mbr
map = /boot/map

delay = 20

default = Linux

image = /vmlinuz
  initrd = /initrd.img
  label = Linux
  read-only

--------------------------------------------------------- 

ANY CLUES??? Please help me :-(

---

### Post by mslonik on 2006-02-05
# cat /proc/partitions

major      minor     #blocks     name
8              0                              sda
8             1                               sda1
8              16                             sdb
8              17                             sdb1
240           0                              cloop0
254           1                              dm-1
254          2                                dm-2
254           3                               dm-3
254           4                              dm-4
254           5                              dm-5
254           6                              dm-6
9               0                             md0
254            7                            dm-7
254           8                             dm-8
254           9                             dm-9
254          10                             dm-10
254          11                            dm-11
254           12                            dm-12
254           13                           dm-13

-----------------------------------------------------------------------

# ls /dev/mapper

+ PV-boot          254,2
+ PV-home          254,5
+ PV-root            254,4
+ PV-swap          254,3
+ PV-zasoby       254,6
+ casper-cow      254,0
+ casper-snapshot 254,1
- control
---------------------------------------------------------------------------

So it looks like wrong indexing. Lilo says about 0xFE07 device. Decimally 0xFE07 = 254 07. Device no. 254, 07 it is dm-7 from /proc/partitions file. In /dev/mapper device 254,07 does not exitst. So I think that problem is a little bit tackled down by me. Unfortunately I am not able to do anything further :-( Lilo is still not workable, as my computer too.

For me it looks like a bug, but I don't know yet to where related: lvm, lilo, dev-mapper???. Where and how should I report this problem further? Please assist me, anyone. I've never before reported a bug. If you are interested in helping me please read the whole thread.

---

