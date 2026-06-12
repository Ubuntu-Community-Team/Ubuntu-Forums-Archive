---
title: "USB automount not working after 8.10 upgrade"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by BkkBonanza on 2008-12-25
Hello,
After my system did an auto-upgrade today (from 8.04 to 8.10 upgrade manager) my 2 usb drives started no longer automounting.
I think something was wonky with the upgrade. I installed 8.04 back when it came out and have been keeping things auto-updated since. But when the 8.10 upgrade first came out I started getting incomplete upgrade messages and the system would never finish the upgrade. Now today there came a kernel update that seemed to have cleared the way and the upgrade finally went through completely. I thought that was good.
However, after that several attempts to turn on/off my external usb drives resulted in them never being detected. They don't even show up in the list given by "fdisk -l". 
Is there some diagnostic cmd I can run to find out if something is wrong with HAL and figure out why the automount has stopped working. Has anyone had problems like this?
Thanks for any suggestions.

PS. After 4 attempts I did get one drive to mount. But then after that repeated tries failed. Both my external usb drives had been working wonderfully and automounted fine up til today.

Chris :)

---

### Post by taurus on 2008-12-25
Did you just unplug the drive or turn off the power when you are finished using it?

---

### Post by BkkBonanza on 2008-12-25
I've tried both. Power off and unplugged. Power on and then plug in. Plug in and then power on. Power on and then unplug then plug in. Pretty much any variation that would have previously worked fine.

---

### Post by taurus on 2008-12-25
I meant did you always power off the drive or unplug the drive right after you used it before it stopped working?  You're supposed to either unmount it or eject it before you unplug it or power it off.  Otherwise, you would corrupt the filesystem on the drive.  That's probably what happens to your drive(s) now.

---

### Post by BkkBonanza on 2008-12-25
No, sorry. I have never unplugged it without unmounting it first. I'm fairly competent with these things. I just don't know where to look for info about what's wrong with automounting and HAL.
Note that this happened and with both my external drives. For some reason one of the drives did manage to mount after 4 attempts to re-power it.

---

### Post by taurus on 2008-12-25
Look at your dmesg.

```
dmesg | tail
```

---

### Post by BkkBonanza on 2008-12-25
Sorry for delay. I tried powering everything down and starting fresh but have same results.
Ran dmesg after start up and then after powering up drive and then again after re-plugging drive. Have absolutely no additional messages.

---

### Post by BkkBonanza on 2008-12-25
Now this is strange. I did some more googling and found a reference to using lsusb to see if the usb device shows up.
So I did "lsusb", and it shows my hub but not the drive.
Then a few seconds later the drives automounts and shows up on it's own. It's as if the lsusb command woke something up... now the drive shows up in lsusb as well.
Any ideas?

---

### Post by BkkBonanza on 2008-12-25
Just turned on 2nd drive and it automounted right away this time (without doing anything more). lsusb also shows it listed now.

---

### Post by BkkBonanza on 2008-12-25
Have done another test. Unmounted both drives and turned them off.
Then turned on first drive to see if it would automount.
It didn't. Nothing in dmesg log either.
Ran lsusb again. And sure enough it woke up again and automounted.
It seems from dmesg that a "usb reset" is causing it to detect new usb devices whereas it's not without that. I presume the reset was caused by lsusb?

Output of dmesg (after the disconnect of previous attempt, and after typing lsusb, follows):

[  227.150299] usb 7-3: reset high speed USB device using ehci_hcd and address 3
[  227.243186] usb 7-3.3: new high speed USB device using ehci_hcd and address 6
[  227.260880] usb 7-3.3: configuration #1 chosen from 1 choice
[  227.261651] scsi7 : SCSI emulation for USB Mass Storage devices
[  227.262055] usb-storage: device found at 6
[  227.262060] usb-storage: waiting for device to settle before scanning
[  227.886076] usb-storage: device scan complete
[  227.886972] scsi 7:0:0:0: Direct-Access     Hitachi  HDP725050GLA360  A52A PQ: 0 ANSI: 2 CCS
[  227.905353] sd 7:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  227.906496] sd 7:0:0:0: [sdb] Write Protect is off
[  227.906503] sd 7:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  227.906507] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  227.907988] sd 7:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[  227.908733] sd 7:0:0:0: [sdb] Write Protect is off
[  227.908739] sd 7:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  227.908743] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  227.908748]  sdb: sdb1
[  227.931080] sd 7:0:0:0: [sdb] Attached SCSI disk
[  227.931150] sd 7:0:0:0: Attached scsi generic sg2 type 0

---

### Post by BkkBonanza on 2008-12-25
Anybody any ideas how to fix this?

---

### Post by ronniet on 2008-12-30
ditto, I'm getting:

reset high speed USB device using ehci_hcd

when I'm trying to transfer songs to my iPod Classic  :(

---

### Post by joshmuffin on 2008-12-30
Could I see your your /etc/fstab file

Open a terminal Accessories > Terminal and type sudo gedit /etc/fstab. Copy and paste the document into a new post.

---

### Post by bsmith1051 on 2008-12-31
I'm having problems, too.  The weird thing is that after about 5 minutes the system spontaneously 'decided' to recognize the flash drive and mount it.  I did nothing to trigger it.  So I really don't think it's a configuration problem, more likely to be a bug in the USB code or an incompatibility with my motherboard.

It might also be a flaky flash-drive, of course.

When the drive was finally recognized, the dmesg says that it's "not running at top speed; connect to a high speed hub."  So it appears to have fallen back to USB 1.1 mode?

P.S. I have a fresh install of 8.10 on an AMD 740G motherboard.

---

### Post by BkkBonanza on 2009-01-01
For joshmuffin, contents of my fstab. It hasn't changed at all since it worked fine. Perhaps the upgrade now requires a change to the usbfs line?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=f651eaca-f066-4767-ac88-057c2aa2f381 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1a0223bf-1e49-4525-8ceb-53bb03b7381b /boot           ext3    defaults        0       2
# /dev/sda3
UUID=929f285f-0b91-43fa-8b5c-f508f5a2787c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
none 		/proc/bus/usb 	usbfs 	devgid=1001,devmode=664 0 0

---

### Post by rapha fanti on 2009-06-14
Hi guys,

Same thing happened to me after 8.4 to 8.10 upgrade. 

It's realy bugging me because, besides not being able to mount drivers that previously worked fine, intrepid seems to also "hide" files, eg my MP3 players doesn't list it's music anymore.

Here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b780c352-a5ba-4b9d-92ff-ba1bd1d12815 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6418dcff-d181-4a29-a2b8-e60a2c5fd155 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Thanks for your help

---

