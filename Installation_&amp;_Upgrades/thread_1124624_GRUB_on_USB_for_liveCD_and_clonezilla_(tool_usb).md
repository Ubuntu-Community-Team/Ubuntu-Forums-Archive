---
title: "GRUB on USB for liveCD and clonezilla (tool usb)"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by jared3227 on 2009-04-13
Hi I am trying to create a usb drive with different tools on it.I first partitioned and formated the usb into 3 partitions I first used the "create a usb startup disk" admin tool to put an 8.10 livecd on the second partition of the usb drive.  that was working fine. then put clonezilla on the 3rd partition and made it bootable with syslinux.  that caused the usb to boot dierctly to the clonezilla bootscreen.  Now i would like to put GRUB on the first partition in order to select which one i would like to boot into. however i cant seem to get this done. copied the /boot/grub files onto the partition.  Then ran 
grub-install --root-directory=/media/disk-2 /dev/sdb
and get a error of 
/dev/sdb does not have any corresponding BIOS drive.
  Just looking for easy detailed instructions on how to install grub so that it will boot into either live clonezilla or ubuntu liveCD and even better if it will also recognize any OS's on any system i put the usb into

thanks

---

### Post by antikristian on 2009-04-13
Disclaimer: I didn't really go through the entire process, but teoretically it should work

Partition the drive like you want
unplug and reinsert memstick
mkfs.ext2 /dev/sdb1 (if this is your first partiton on the memstick)

Use unetbootin to install grub on the first partition (check "show all drives" and select the first partition on the memorystick)

Backup grub
dd if=/dev/sdb1 of=grub.img bs=1024
Backup MBR
dd if=/dev/sdb of=mbr.img bs=512 count=1

Install other operatingsystems manually or with unetbootin, I concidered customizing [This]("http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/")

when you are done, reverse the dd process with 
First backup, this entire process isn't really tested:-P
dd if=/dev/sdb of=memstick.img bs=1024
Then
dd if=grub.img of=/dev/sdb1 bs=1024
dd if=mbr.img of=/dev/sdb bs=512

Customize the /boot/grub/menu.lst on the grub partition and you might be good to go:-P

Gotchas:
syslinux configlines would need to be modified to work in grub, but they might give you a hint of what to put in grub, You would have to either install grub on each of the partitons and chainload, or configure everything on the grub partiton. As far as I know, you can't chainload to syslinux, since I belive it only installs itself in mbr

use labels on the partitions and specify those in the fstab files
Not sure if you can specify labels in grub, but maybe. The reason why you should use labels, is because the memory stick might be /dev/sdb on one machine and /dev/sdd on another, insert a second usb stick or memory card on one computer and you could have diffrent numberings on the same computer.

---

### Post by jared3227 on 2009-05-01
thanks you gave me a good start.  ended up installing clonezilla with Unetbootin, then installed livecd with unetbootin, and then grub with unetbootin each on a separate partition. not the prettiest but it works,

---

