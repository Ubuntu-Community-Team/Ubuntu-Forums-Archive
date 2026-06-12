---
title: "Boot error - after installing ubuntu server"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by heen2001 on 2009-02-22
I've been scouring the posts for an answer to this problem - and i've tried a number of things but all to no avail over the course of the last 5 days.

I have an Artigo A2000, VIA C7-D chip, 
2Gb RAM, 
2x1Tb WD HDD (for data), 
4Gb Kingston CF (to install OS on)

I am trying to simply install ubuntu server 8.10 onto this system, with software RAID 0 across the HDDs and install ubuntu to the CF card. Sounds simple enough, here is what i've done so far.

1. Using unetbootin on vista i created a bootable USB key with a 8.10 server iso. 

2. I managed to install 8.10 to the CF card using this, during the install i formatted the 2 HDD for the RAID Array and configured a RAID 0 Array and set its mount point as '/data/, also formatted the CF card with 3Gb for Ubuntu (ext3) mount point '/ ' and remaining 1Gb for swap.

3. so far so good, continued the install - all went without any problems.

4. went to reboot - and I get "Boot Error" (yes I have set the boot priority in the BIOS to boot from the CF card now)

Now from reading forums, reinstalling trying different versions of ubuntu (8.04) and even playing about with grub - i'm still getting the same error. I am thinking this is something associated with grub, just from what i've been reading. If it isn't i'd be most grateful if someone can tell what it might be,

These are the devices I have,
hd0 - 8Gb USB Key, used to install the OS
hd1 hd2 - 1Tb WD HDD
hd3 - 4gb CF


This is my /boot/grub/device.map

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd


This is my /boot/grub/menu.lst entries

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd3,0,0)
uuid		a9d47223-d717-46f7-8b11-1bcdc2a55be7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a9d47223-d717-46f7-8b11-1bcdc2a55be7 ro quiet splash quiet 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		a9d47223-d717-46f7-8b11-1bcdc2a55be7
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=a9d47223-d717-46f7-8b11-1bcdc2a55be7 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		a9d47223-d717-46f7-8b11-1bcdc2a55be7
kernel		/boot/memtest86+.bin
quiet



If anyone can point in the right direction or has an answer to my problem it would be very much appreciated - as i'm losing the will to live to continue toying with this. 

Thanks

heen2001 :(

---

### Post by komputes on 2009-02-24
When you install ubuntu it will modify the MBR, usually on the hd0 MBR 512 bytes of the drive. This is a pointer to a partition which has a bootable operating system. grub-install will help you reset that MBR. You will need to boot into a livecd environment to do this.

Mount the ubuntu installation "/" (in this case it will be mounted to /media/disk) and know which device you would like to install the MBR onto (in this case /dev/sda). After this command the BIOS will boot and pass control over to the "master disk" /dev/sda which will read the pointer in the first 512 bytes which points it to /boot on /media/disk (/dev/sda1)

When booting, into grub you may need to edit the rood disk of the disk to get it to boot well. this is due to the disk thinking it is the second disk loaded, but when the bios boots from it it is now seen as the first disk for this you need to change (hd1,0) to (hd0,0)

grub-install --root-directory=/media/disk/ /dev/sda

Now whatever drive /dev/sda is, your BIOS should be pointing to that as #1 in the boot sequence.

---

### Post by heen2001 on 2009-02-26
Thanks for the help komputes! - it worked!!!

all hail ubuntu forums.

---

