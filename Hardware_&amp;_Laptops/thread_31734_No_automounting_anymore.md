---
title: "No automounting anymore"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by sammy44 on 2005-05-04
Hi,

since a few days i have following problem : when i insert a CDROM or plug in my usb stick Ubuntu wont automount the device. But when i click under Computer-> cdrom(2)
nautilus opens a window with the cd and suddenly the icon appears on my desktop.

When i plug in my usb stick, i have to type "mount /dev/sda1 /media/usbdisk" to access it, there is no other way.

THis situation is quite anoying because my Ubuntu is also used by my girlfriend and she doesnt know how to mount, she wants to use !!

fstab  + mtab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=michi 0 0

---

### Post by capper308 on 2005-05-09
I have this same problem.  Could someone with the skills please tell us what to do?

---

### Post by SilvioTO on 2005-05-12
The same problem for me. I installed Hoary on my friend pc; after one day, cdrom, cdrw and usb stick don't automount.

---

### Post by Alexander Kirillov on 2005-05-12
[QUOTE=sammy44]Hi,

since a few days i have following problem : when i insert a CDROM or plug in my usb stick Ubuntu wont automount the device. But when i click under Computer-> cdrom(2)
nautilus opens a window with the cd and suddenly the icon appears on my desktop.

When i plug in my usb stick, i have to type "mount /dev/sda1 /media/usbdisk" to access it, there is no other way.
[/QUOTE]
 Can be the infamous [DBUS/HAL bug](http://ubuntuforums.org/showthread.php?t=27087).

---

### Post by derrick1985 on 2005-05-14
[QUOTE=Alexander Kirillov]Can be the infamous [DBUS/HAL bug](http://ubuntuforums.org/showthread.php?t=27087).[/QUOTE]

Yeah, I just got that today though. For some reason, my stick no longer automounts, did the command, and now it will.

Weird thing this is.... yes...

---

### Post by derrick1985 on 2005-05-14
Well, i finally got po'ed enought, that I change all lines of hoary to breezy, and dist-upgrade'd, and problem no more.

---

### Post by Ali_Baba on 2005-05-14
Thanks derrick1985 :) With that dist-upgrade got that bug fixed.Noticed it today with my cdrom drive.

---

### Post by biodiesel-bri on 2005-05-14
I've got the same problem.  I have several USB hd based devices and none of them are automounting anymore, I believe since my last synaptic upgrade.

/etc/init.d/hotplug restart has no effect

pmount /dev/sda1 *does* mount the device though.  I wonder what the problem is?  I'd rather not upgrade to breezy so soon.

-B

```
May 14 11:23:28 localhost kernel: usb 1-2.3: new full speed USB device using uhci_hcd and address 6
May 14 11:23:28 localhost kernel: usb 1-2.3: not running at top speed; connect to a high speed hub
May 14 11:23:28 localhost kernel: Initializing USB Mass Storage driver...
May 14 11:23:28 localhost usb.agent[10932]:      usb-storage: loaded successfully
May 14 11:23:28 localhost kernel: scsi2 : SCSI emulation for USB Mass Storage devices
May 14 11:23:28 localhost kernel: usbcore: registered new driver usb-storage
May 14 11:23:28 localhost kernel: USB Mass Storage support registered.
May 14 11:23:33 localhost kernel:   Vendor: PENTAX    Model: DIGITAL_CAMERA    Rev: 1.00
May 14 11:23:33 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
May 14 11:23:33 localhost kernel: SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
May 14 11:23:33 localhost kernel: sda: Write Protect is off
May 14 11:23:33 localhost kernel: SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
May 14 11:23:33 localhost kernel: sda: Write Protect is off
May 14 11:23:33 localhost kernel:  /dev/scsi/host2/bus0/target0/lun0: p1
May 14 11:23:33 localhost kernel: Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
May 14 11:23:33 localhost scsi.agent[11025]:      sd_mod: loaded sucessfully
```
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

```

---

### Post by derrick1985 on 2005-05-14
> **biodiesel-bri]I've got the same problem.  I have several USB hd based devices and none of them are automounting anymore, I believe since my last synaptic upgrade.

/etc/init.d/hotplug restart has no effect

pmount /dev/sda1 *does* mount the device though.  I wonder what the problem is?  I'd rather not upgrade to breezy so soon.

-B

```
May 14 11:23:28 localhost kernel: usb 1-2.3: new full speed USB device using uhci_hcd and address 6
May 14 11:23:28 localhost kernel: usb 1-2.3: not running at top speed said:**
> :      usb-storage: loaded successfully
May 14 11:23:28 localhost kernel: scsi2 : SCSI emulation for USB Mass Storage devices
May 14 11:23:28 localhost kernel: usbcore: registered new driver usb-storage
May 14 11:23:28 localhost kernel: USB Mass Storage support registered.
May 14 11:23:33 localhost kernel:   Vendor: PENTAX    Model: DIGITAL_CAMERA    Rev: 1.00
May 14 11:23:33 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
May 14 11:23:33 localhost kernel: SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
May 14 11:23:33 localhost kernel: sda: Write Protect is off
May 14 11:23:33 localhost kernel: SCSI device sda: 498176 512-byte hdwr sectors (255 MB)
May 14 11:23:33 localhost kernel: sda: Write Protect is off
May 14 11:23:33 localhost kernel:  /dev/scsi/host2/bus0/target0/lun0: p1
May 14 11:23:33 localhost kernel: Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
May 14 11:23:33 localhost scsi.agent[11025]:      sd_mod: loaded sucessfully
```
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

```


Well, if you don't like breezy, you can always downgrade back to hoary.

---

### Post by mrt on 2005-05-15
[QUOTE=derrick1985]Well, i finally got po'ed enought, that I change all lines of hoary to breezy, and dist-upgrade'd, and problem no more.[/QUOTE]

wow, thanks for suggesting this.  I was pulling my hair out over this one for a while.

---

### Post by derrick1985 on 2005-05-15
[QUOTE=mrt]wow, thanks for suggesting this.  I was pulling my hair out over this one for a while.[/QUOTE]

Glad it's working out for you.

---

### Post by biodiesel-bri on 2005-05-16
Is breezy stable enough, or am I going to be swapping one problem for another?

---

### Post by SilvioTO on 2005-05-16
My opinion is to use prudence, mount by hand for now, mount disk applet on the panel it's confortable, easy and fast solution.

---

### Post by mike'o on 2005-05-16
Hi  :) 

There is another thread on this one at:
[http://www.ubuntuforums.org/showthread.php?t=27087](http://www.ubuntuforums.org/showthread.php?t=27087)

Please take a look and if you have any thoughts on this, let us know.

Mike

---

### Post by rkinder on 2005-05-22
Shot in the dark - is the user running the desktop a member of the 'plugdev' group? If not, automounting won't work... as I found out after about 2 hours of stuffing around :)

---

### Post by WorLord on 2005-05-27
See thread [here](http://ubuntuforums.org/showthread.php?t=37488) for solution.

---

