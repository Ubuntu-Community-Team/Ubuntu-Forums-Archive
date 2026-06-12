---
title: "USB mp3 player won't work after 8.04 upgrade"
date: 2008-04-28
forum: Hardware
---

### Post by mic_la on 2008-04-28
My MP3 player (Sony A816) used to "just work" with Ubuntu 7 / Sony Vaio laptop. Somehow since the upgrade to 8 it seems to have stop, meaning that when connected, its icon does not appear on the desktop. I show the lsusb and mount results below.
note 1: my USB mouse is working perfect
note 2: usbview complained about "can not open /proc/bus/usb/devices" and ask to verify USB was compiled in kernel and installed and usbdevfs is mounted. The "mount" command output is here and there is no usbdevfs:
mount. So I am thinking something is not being mount but used to. ANy clue will be aprecianted. thanks, michel_la
$mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)


lsusb shows:
michel@michel-laptop:~$ lsusb
Bus 007 Device 002: ID 054c:0325 Sony Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 05ca:1839 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 044e:300d Alps Electric Co., Ltd 
Bus 001 Device 001: ID 0000:0000

---

### Post by ChameleonDave on 2008-04-28
Is it actually this particular MP3 player, or are you saying that all USB mass-storage devices fail to mount?  Or just fail to automount?

---

### Post by mic_la on 2008-04-28
I do not have other USB storage device to test with, but the issue can be summarized like: the  mp3/"mass storage" device is failing to automount.
I looked a bit more into it - in case it helps :
~$ sudo mount -f usbdevfs
mount: can't find usbdevfs in /etc/fstab or /etc/mtab

---

### Post by mic_la on 2008-04-28
Hey, I made some progress but not a solution yet:
after doing: sudo mount -t usbfs none /proc/bus/usb/
usbview is able to see my device. information is displayed below. unfortunately the automount is not working (icon does not show up after removing/inserting the device)

WALKMAN
Manufacturer: Sony
Serial Number: 491CA4005740
Speed: 480Mb/s (high)
USB Version:  2.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 054c
Product Id: 0325
Revision Number:  1.00

Config Number: 1
	Number of Interfaces: 1
	Attributes: 80
	MaxPower Needed: 500mA

	Interface Number: 0
		Name: usb-storage
		Alternate Number: 0
		Class: 08(stor.) 
		Sub Class: 05
		Protocol: 50
		Number of Endpoints: 3

			Endpoint Address: 81
			Direction: in
			Attribute: 2
			Type: Bulk
			Max Packet Size: 512
			Interval: 0ms

			Endpoint Address: 02
			Direction: out
			Attribute: 2
			Type: Bulk
			Max Packet Size: 512
			Interval: 0ms

			Endpoint Address: 83
			Direction: in
			Attribute: 3
			Type: Int.
			Max Packet Size: 2
			Interval: 32ms

---

### Post by Bloch on 2008-04-29
automount of vfat memory devices can be affected by the upgrade to Hardy 8.04

Here is a solution:
Open Applications > System Tools > Configuration Editor

Go to the key system > storage > default_options > vfat
Edit the mount_options key by removing the usefree option.

You may need to reboot.
The devices should then automount when plugged in: i.e. the icon will appear on the desktop.

I emailed one of the developers involved, Martin Pitt.
> That's indeed the right solution. 'usefree' is deprecated in Hardy (it
was only a temporary hack in Gutsy), and thus the gnome-mount
option 'usefree' has been removed in Hardy again.

You need it in Gutsy to avoid minute-long hangs when mounting a VFAT
drive. In Hardy this was fixed properly in the kernel.

---

### Post by mic_la on 2008-04-29
thanks... but there was no usefree there. I could see the following:
shortname=mixed
uid=
utf8
umask=077
exec
flush
I also found about something new thanks to your suggestion to go to the configuration editor:
I was looking at the Nautilus setting and added between others the "Computer" icon to my desktop. Now, when I insert the USB device, then the "USB drive" icon shows up in the "Computer - File browser" window (but not on the desktop). Oddly enough,  when double-clicking on this "USB drive" icon, the error "Unable to mount location can't mount file" appears.
Thanks again for the suggestion,
mic_la

---

### Post by jmthomas on 2008-06-25
I am also having that same problem with USB drives.

Is there a fix somehow using the configuration editor?

---

