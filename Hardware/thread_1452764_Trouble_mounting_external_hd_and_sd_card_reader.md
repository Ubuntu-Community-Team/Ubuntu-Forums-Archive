---
title: "Trouble mounting external hd and sd card reader"
date: 2010-04-12
forum: Hardware
---

### Post by dive_nerd on 2010-04-12
I know there are about a thousand posts for this issue and I think I've read them all to no avail. My laptop is an EEE pc and I'm running Netbook Remix 9.04. I currently have 2 external hard drives and one is working fine. The other one was working until it took a dive for the floor, but I want to see if it will work again. It powers on fine, makes a few weird noises then seems to be okay. When I try to access the drive I get the error msg 
'Unable to mount location. Can't mount file.'

My laptop has an internal sd card reader that I can't get working either. I get the error msg 
'Cannot mount volume. Invalid mount option when attempting to mount the volume.'
It then tries to access the drive and this msg pops up after a min or so.
'DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.'

This is my fstab:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=d98f8923-3164-4d5d-a5cb-73c6e687d84b  /               ext3  relatime,errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=16ceb39b-5d63-43b7-8c93-c9a655ef3a65  none            swap  sw                          0  0
/dev/sdc1                                  /media/STORAGE  vfat  owner,users                 0  0


Any help would rock my socks!

---

### Post by dive_nerd on 2010-04-13
I found a great tutorial on mounting external drives here: [http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux](http://www.linuxconfig.org/Howto_mount_USB_drive_in_Linux). And I was able to get my SD card reader working! Yeah!

But I'm still having problems with my other drive. Fdisk tells me 'Disk /dev/sdc doesn't contain a valid partition table'

I don't really want to use gparted to fix since it will format the drive. I know this drive was working fine at one point, but after it got dropped it never worked properly and may be permanently damaged.
Any advice?

---

