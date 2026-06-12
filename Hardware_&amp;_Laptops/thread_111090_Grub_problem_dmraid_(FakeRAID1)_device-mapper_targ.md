---
title: "Grub problem? dmraid (FakeRAID1): device-mapper target type &quot;mirror&quot; not in kernel"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by lptr on 2006-01-01
Again regarding to: [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

I recently did what the author has described there but not into RAID0 but on RAID1 (mirror). So far all things seem to be ok when I booting with Breezy LiveCD loading dmraid drivers.

[SIZE="1"]# dmraid -tay
pdc_deiadfjehd: 0 312500000 mirror core 2 64 nosync 2 /dev/sda 0 /dev/sdb 0
pdc_deiadfjehd1: 0 76003452 linear /dev/mapper/pdc_deiadfjehd 63
pdc_deiadfjehd5: 0 233295867 linear /dev/mapper/pdc_deiadfjehd 76003578
pdc_deiadfjehd6: 0 3196872 linear /dev/mapper/pdc_deiadfjehd 309299508
[/SIZE]

I successfully mounted device and installed Breezy in chroot onto target
[SIZE="1"]# mount -t ext3 /dev/mapper/pdc_deiadfjehd1 /target/
[/SIZE]

But when it comes to booting from RAID then I got stuck into /bin/sh. The resulting messages are the following:

[SIZE="1"]device-mapper: unknown target type
ERROR: device-mapper target type "mirror" not in kernel
ERROR: dos: reading /dev/mapper/pdc_deiadfjehd[No such file or directory]
RAID set "pdc_deiadfjehd" already active
ERROR: dos: reading /dev/mapper/pdc_deiadfjehd[No such file or directory]
    /dev/cdrom: open failed: No medium found
    Unable to find volume group pdc_deiadfjehd
[/SIZE]

[SIZE="1"]# dmraid -V
dmraid version:         1.0.0.rc9 (2005.09.23)
dmraid library version: 1.0.0.rc9 (2005.09.23)
device-mapper version:  4.4.0
[/SIZE]

[SIZE="1"]Kernels
RAID1 installed: 2.6.12-10-386
LiveCD: 2.6.12-9-386
[/SIZE]

I did some research and found this:
[SIZE="1"]http://www.redhat.com/archives/dm-devel/2005-February/msg00039.html[/SIZE]
It tells "The mirror target is not compiled in and there is no dm-mirror.ko available." This infos are quite old and in LiveCD it does mount. Installed kernel is newer than that one form LiveCD. So I expect that I probably missconfigured GRUB?

device.map
```
(hd0) /dev/mapper/pdc_deiadfjehd

```

menu.list
```
...
title  Ubuntu, kernel 2.6.12-10-386 
root  (hd0,0)
kernel  /boot/vmlinuz-2.6.12-10-386 root=/dev/mapper/pdc_deiadfjehd ro quiet splash
initrd  /boot/initrd.img-2.6.12-10-386
savedefault
boot
...

```

What I am doing wrong? 
Any hints are highly appreciated.

---

### Post by bbrazil on 2006-01-06
Have you found a solution to this problem?

I've having a VERY similar issue...

---

### Post by lptr on 2006-01-07
[QUOTE=bbrazil]Have you found a solution to this problem?

I've having a VERY similar issue...[/QUOTE]

No. Sadly to say, that I found no 'direct' solution, yet. For our case I found a - hm... - quite usable way of having 'just and only' data on raid. Boot drive is IDE. A RAID1 only solution after all thinking I find definitively distrustable.

:idea: Our three harddrives poor man's 'high available solution' is looking like this:
Breezy is on hda1, hda2 is 'add_data', hda5 swap. Loading dmraid from hda1 (Breezy), mounting /dev/pdc_xyzanything on /srv/. This will keep realtime data. During night hours when nobody is using data (especially this one very important Jet-database I discribed in previous post) I let machine copying data over to add_data on hda2 via Cron job. Additionally there happens a manual copy (could be cron controlled, too) on a external USB drive and another workstation. This is a three times redundancy and does seem sufficient to me. If anything breaks with controller(s), the possibilities to access IDE harddrive from another machine to grab data from previous day off is quite good.

dmraid: This seems to be a classical chicken/egg problem. If there is no driver that can be loaded during boot time, there is no OS ( obviously - initramfs does not do the job :( ). And Grub is not 'the' OS so it is unable to load drivers. It is only _able_ to point anywhere to point to a location on harddrive that will load harddrive drivers, then. At the point where the first access on 'unRAIDed' sda1 occurs drive is mounted. If driver tries loading RAID1 on a already mounted partition it has to break. 

Maybe this boot dmraid will work with some controllers while doing some - hm - magic? But anyways: I don't expect this solution working on every fakeraid controllers like mine here which is of brand 'Promise'. 

Could be, that I am completely wrong 8-) but until the HW manufacturer can proof me the oposite I will not trust HW-RAID1 in this low price segment

rob*

---

### Post by bbrazil on 2006-01-08
Just for fun, I tried rebuilding the kernel with DM_MIRROR compiled in...  

That gets me over the "boot hump". Now I just need to figure out why none of my devices work...

---

### Post by bbrazil on 2006-01-11
Eureka!

Here's what I did...

First I found an old 4GB IDE drive I wasn't using for anything.  I blew away the partitions on that drive and installed Ubuntu from the vanilla installation disks.

Then I installed dmraid, the kernel sources, and various packages required to build kernels (build-essential, libncurses-dev, g++).

I built a kernel with Device Mapping and Mirroring built in (from menuconfig, it's under Device Drivers -> <something> (LVM & RAID)).  Follow the appropriate howto for building kernels.

I then followed the directions for rebuilding initramfs from the FakeRaidHowto.  

Shut down, plug in the SATA drives, reboot.

The RAID array should now be visible.  Partition and format some partitions, as per the FakeRaidHowto.  For simplicity, I created 2 partitions: swap and root.

Mount the root partition and use rsync to copy everything over:
sudo rsync -av / /mnt
(if you have more than one partition, you may need to do them separately)

chroot to /mnt and do the grub setup from FakeRaid Howto.  Some trickery was involved here.  I found that, on my machine, hd0 was the IDE drive, hd1 and hd2 were the physical SATA drives, so I had to define the new device as (hd3).  However, in the menu.lst file, I had to refer to it as (hd0).

Edit the /etc/fstab to point at the RAID array, shutdown, remove the IDE drive, reboot, and I was in business.

---

### Post by steinb on 2006-01-23
Can you post your menu.lst for grub and the dmraid scripts for /local-top/ and /hooks/?

---

### Post by bbrazil on 2006-01-24
[QUOTE=steinb]Can you post your menu.lst for grub and the dmraid scripts for /local-top/ and /hooks/?[/QUOTE]
My menu.lst.
The first 2 entries are for the kernel residing on the RAID array.
The second 2 entries are for the same kernel residing on the scrap IDE drive.
Bear in mind mine RAID array has 2 partitions: swap and ext3
```
title           Ubuntu, kernel 2.6.12 Default
root            (hd0,1)
kernel          /boot/vmlinuz root=/dev/mapper/nvidia_eecgdbfe2 ro quiet splash
initrd          /boot/initrd.img
savedefault
boot

title           Ubuntu, kernel 2.6.12 Default (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz root=/dev/mapper/nvidia_eecgdbfe2 ro single
initrd          /boot/initrd.img
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic Previous
root            (hd0,0)
kernel          /boot/vmlinuz.old root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img.old
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic Previous (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz.old root=/dev/hdc1 ro single
initrd          /boot/initrd.img.old
boot
```
The scripts are the same as the FakeRaidHowto scripts.  See the wiki for more info on that.

---

