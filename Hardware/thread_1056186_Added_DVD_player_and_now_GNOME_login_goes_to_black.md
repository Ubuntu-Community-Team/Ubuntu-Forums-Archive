---
title: "Added DVD player and now GNOME login goes to black"
date: 2009-01-31
forum: Hardware
---

### Post by davidself1001 on 2009-01-31
I put an old DVD ROM into my system from one of my son's old PCs and now I never get to the GNOME login screen.  I see the usplash progressing all the way to the end and when I normally get the login I get a black screen and my monitor shows not signal (ie light goes amber).  If I do a ctrl-alt-backspace and then hit ctrl-alt-f2 I can get the a virtual terminal.  If I just exit from the terminal then I go to the login prompt.  Obviously the DVD has some issue.  i also have a CD as the master and removed the jumper from the DVD hopeing to set it as a slave.  Once up when I go to HW info it finds the DVD ROM but says unknown device.  Help

---

### Post by davidself1001 on 2009-01-31
Decided to try to get the DVD ROM working to see if that eliminates my problem on bootup.  I have the fstab set as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=602dcfdc-c0bf-4ed4-a540-301706fb343a /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=44cc141f-bdf8-45fc-bac4-eaa6304f101c none            swap    sw              0       0
/dev/sdb1 /home ext3 defaults,errors=remount-ro 0 1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# For USB access with Virtualbox
usbfs /proc/bus/usb usbfs auto 0 0

When I put a DVD in I get "Cannot Mount..." and details show "no media found".  Could that be because of the way I have the fstab set?
none	/proc/bus/usb	usbfs	devgid=119,devmode=664	0	0

---

### Post by davidself1001 on 2009-01-31
Ok I am making progress (i feel like i am talking to myself).  The DVD is now recognized, I have changed to fstab so that it successfully mounts.  I don't crash when GNOME login starts (although I do get some strange graphic behaviors).  Now I just need to figure out how to boot from the DVD.   I checked the bios and it has my CD ROM as the first boot device.  My DVD is a slave off the CD.  Do I need to make the DVD the master or will the system boot from the DVD if is is a slave off the CD?

---

