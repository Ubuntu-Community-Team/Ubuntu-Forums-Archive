---
title: "How to mount a disk without user interaction?"
date: 2013-06-14
forum: Hardware
---

### Post by LeoTheSecond on 2013-06-14
Hi,

if I type into a terminal

sudo udisksctl mount --block-device /dev/disk/by-uuid/<UUID> --no-user-interaction

I'm getting a line to type in my password. How can I avoid this?

And what would be the content and file extension (".txt"?) of an autostart script to provide mounting  while booting? Automounting is on, but does not work.

Background: Lubuntu 13.04 x64 as guest under VirtualBox 4.2.12, host is Windows 8 Pro x64.

---

### Post by NikTh on 2013-06-14
If you prefix a command with sudo, then the user=root password is needed to execute the command. 

The case of yours is a special case on VirtualBox VM , so things might be different here. Never used the automount option in VB. 
See this if helps : [http://askubuntu.com/questions/52328/mount-virtualbox-sharedfolder-in-ubuntu-vm-on-boot](http://askubuntu.com/questions/52328/mount-virtualbox-sharedfolder-in-ubuntu-vm-on-boot)

and also tell us , what is the host OS ? (Windows, another Linux ? ) 

Thanks

---

### Post by LeoTheSecond on 2013-06-14
Hi, NikTh, host is, as added above, Windows 8.
I'm using a shared folder without problems, can be used immediately after guest booting.
VirtualBox Extension Pack and Guest Additions are installed.
Using command line without "sudo" results in error "Not authorized to perform operation" although I'm logged in as administrator and member of group vboxsf.
With automount on I meant mount options in Lubuntu disks application.

Content of fstab is:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=39b21934-1f83-2455-b12e-2f8921dd207c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d27130d7-03ac-417c-124f-2017362ca193 none            swap    sw              0       0

Problem volume is sdb1.

---

### Post by NikTh on 2013-06-14
And what is this /dev/sdb1 partition ? A partition on another VM machine (in VB) ?  , a usb-stick or usb-HDD 
Open lxterminal and issue the following command 

```
sudo fdisk -l
```

post back here the results. 

Thanks

---

### Post by LeoTheSecond on 2013-06-14
[COLOR=#000000] /dev/sdb1 is another VirtualBox disk within the same virtual machine.

[/COLOR]Meanwhile I did the following:

- typing [COLOR=#008000]sudo blkid i[/COLOR]nto terminal to get UUID of the problem volume sdb1
- typing [COLOR=#008000]sudo leafpad /etc/fstab [/COLOR]into terminal
- adding this line at the end of fstab:
[COLOR=#008000]UUID=47c218f7-ga50-4954-b6f6-f2673e09cb1w    /media/[/COLOR][COLOR=#0000cd]myfolder[/COLOR][COLOR=#008000]        ext4        defaults     0       0[/COLOR]
Last line of fstab is empty.
- reboot

Now volume is mounted after booting, thanks, NikTh.

---

