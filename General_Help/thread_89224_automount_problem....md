---
title: "automount problem..."
date: 2005-11-12
forum: General Help
---

### Post by cypher35 on 2005-11-12
After recently starting out with a fresh install of breezy about a week ago, i was able to put dvds or cds into either of my two drives (a cd burner at /dev/hdc/ and a dvd drive at /dev/hdd/) and it would be auto-mounted and displayed in konqueror.

However after trying it just today, they no longer appear to be working.  I don't really use the drives very often, so i'm not sure what i did to break it.  It could have been anything i've done over the last week.

Now when i put a udf data dvd in the drive, it says:
> An error occurred while loading **media:/hdd**:
The file or folder media:/hdd does not exist.

Strangely, going to media:/ now shows only the floppy drive and nothing else.  I'm pretty sure the drives are supposed to show up in that list.  Or do they only show up there after they have been mounted?


here is my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>	<options>       	<dump>  <pass>
proc		/proc		proc	defaults		0	0
/dev/hda3	/		ext3	defaults,errors=remount-ro 0	1
/dev/hda6	none		swap 	sw			0	0
/dev/hdd	/media/cdrom0	udf,iso9660 ro,user,noauto	0	0
/dev/hdc	/media/cdrom1	udf,iso9660 ro,user,noauto	0	0
/dev/fd0	/media/floppy0	auto	rw,user,noauto		0	0

# Extra Volumes
/dev/hda1	/vol/C		ntfs	user,nls=utf8,umax=022,ro,noauto 0 0
/dev/hda5	/vol/Backup	vfat	user, noauto		0	0
/dev/sdc5	/vol/Q 		ext3	user, noauto		0	0
/dev/mapper/pdc_dbicecjhbc5 /vol/X ext3	user, noauto		0	0
```
Everything under #Extra Volumes was added by me...  i can't remember if i touched anything above it or not.

Going to the "Disk & Filesystems" module in System Settings, you can see that it doesn't appear to recognise the drive's settings either even though they are clearly there in /etc/fstab:
[IMG]http://i2.photobucket.com/albums/y7/cypher35/diskmanager.png[/IMG]
Modifying the above settings appears to serve no purpose other than to screw up the spacing of my fstab file...

If it helps, "dmesg | tail" yeilds:
```
[4296229.194000] cdrom: This disc doesn't have any tracks I recognize!
```

and "id hal" yeilds:
```
uid=111(hal) gid=111(hal) groups=111(hal),24(cdrom),25(floppy),46(plugdev)
```

and searching through "lshal", i found the following entries for my two drives:
```
udi = '/org/freedesktop/Hal/devices/storage_serial_3F11002489_0175'
  info.addons = {'hald-addon-storage'} (string list)
  storage.policy.desired_mount_point = 'cdrecorder'  (string)
  storage.policy.mount_filesystem = 'auto'  (string)
  storage.policy.should_mount = true  (bool)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_3F11002489_0175'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_3F11002489_0175'  (string)
  storage.cdrom.write_speed = 9526  (0x2536)  (int)
  storage.cdrom.read_speed = 9526  (0x2536)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.dvdplusrw = false  (bool)
  storage.cdrom.dvdplusr = false  (bool)
  storage.cdrom.dvdram = false  (bool)
  storage.cdrom.dvdrw = false  (bool)
  storage.cdrom.dvdr = false  (bool)
  storage.cdrom.dvd = false  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.firmware_version = '1.0G'  (string)
  storage.serial = '3F11002489 0175'  (string)
  storage.requires_eject = true  (bool)
  storage.hotpluggable = false  (bool)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.product = 'CR-48XGTE'  (string)
  storage.removable = true  (bool)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_1106_571_ide_1_0'  (string)
  storage.drive_type = 'cdrom'  (string)
  storage.vendor = ''  (string)
  storage.model = 'CR-48XGTE'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.media_check_enabled = true  (bool)
  storage.no_partitions_hint = true  (bool)
  storage.bus = 'ide'  (string)
  block.is_volume = false  (bool)
  block.minor = 0  (0x0)  (int)
  block.major = 22  (0x16)  (int)
  block.device = '/dev/hdc'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/pci_1106_571_ide_1_0'  (string)
  linux.sysfs_path_device = '/sys/block/hdc'  (string)
  linux.sysfs_path = '/sys/block/hdc'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_DM_2000TE'
  info.addons = {'hald-addon-storage'} (string list)
  storage.policy.desired_mount_point = 'cdrom'  (string)
  storage.policy.mount_filesystem = 'auto'  (string)
  storage.policy.should_mount = true  (bool)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_DM_2000TE'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_DM_2000TE'  (string)
  storage.cdrom.write_speed = 0  (0x0)  (int)
  storage.cdrom.read_speed = 2816  (0xb00)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.dvdplusrw = false  (bool)
  storage.cdrom.dvdplusr = false  (bool)
  storage.cdrom.dvdram = false  (bool)
  storage.cdrom.dvdrw = false  (bool)
  storage.cdrom.dvdr = false  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.cdrw = false  (bool)
  storage.cdrom.cdr = false  (bool)
  storage.firmware_version = '5.BV'  (string)
  storage.requires_eject = true  (bool)
  storage.hotpluggable = false  (bool)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.product = 'DM-2000TE'  (string)
  storage.removable = true  (bool)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_1106_571_ide_1_1'  (string)
  storage.drive_type = 'cdrom'  (string)
  storage.vendor = ''  (string)
  storage.model = 'DM-2000TE'  (string)
  storage.automount_enabled_hint = true  (bool)
  storage.media_check_enabled = true  (bool)
  storage.no_partitions_hint = true  (bool)
  storage.bus = 'ide'  (string)
  block.is_volume = false  (bool)
  block.minor = 64  (0x40)  (int)
  block.major = 22  (0x16)  (int)
  block.device = '/dev/hdd'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/pci_1106_571_ide_1_1'  (string)
  linux.sysfs_path_device = '/sys/block/hdd'  (string)
  linux.sysfs_path = '/sys/block/hdd'  (string)
```

I'm listing these things out because in the other threads that i have found similar to this, these bits of information were requested.


Now for some reason, i appear to be able to automount cds, but not dvds.  I don't know if this is because they use iso9660 instead of udf or if it is some other reason.  I can manually mount it when there is a dvd in the drive by typing "mount /dev/hdd", but when i use this method, no entry is made in "media:/" and no icon appears on the desktop.

---

### Post by aysiu on 2005-11-12
Sounds as if you should file a [bug report](https://bugzilla.ubuntu.com/).

---

### Post by DoeRayMe on 2005-11-12
same here aswell

---

### Post by mlomker on 2005-11-12
My system doesn't show a mount point in that disk tool, even when a disc is mounted.  Most of the graphical applets in Breezy don't work well, it seems.

I have no problem with the automounting of DVD data discs.  Do you have all the device icons enabled in kcontrol?  **kdesu kcontrol** and then look under Desktop, Behavior, Device Icons.

---

### Post by DoeRayMe on 2005-11-12
yeah, i think its a rc1 bug, as it worked in beta2 for me

doesnt even show an icon on the desktop for mounted or unmounted cd/dvd or anything

---

### Post by cypher35 on 2005-11-12
What i don't understand is how it could be so complicated to mount a disk once it's inserted.  Can't it just call "mount /dev/hdd" like i do?

I don't really care if it pops up in a new window, or if a fancy icon appears on the deskop...  It should at *least* be able to mount it.

Does anyone know what function or process is responsible for mounting it?

Fron what i've gathered "ivman" is responsible for opening the window (which is apparently the only part of the process that works...), but what process handles the actual mounting?

---

### Post by jeremy on 2005-11-13
[QUOTE=aysiu]Sounds as if you should file a [bug report](https://bugzilla.ubuntu.com/).[/QUOTE]
I filed a bug report 3 weeks ago, it is at [http://bugzilla.ubuntu.com/show_bug.cgi?id=18211](http://bugzilla.ubuntu.com/show_bug.cgi?id=18211)
Please add to it.

---

### Post by mlomker on 2005-11-13
[QUOTE=cypher35]but what process handles the actual mounting?[/QUOTE]

pmount

---

### Post by tseliot on 2005-11-16
I have the same problem but I have find a workaround:

right click on a free space of the desktop and select

Create new/Link to device/DVD-Rom Device (or Harddisk device, etc.)

write the name of the link in the "General" page (e.g. "pioneer" or "burner", etc.)

click on the Device section:
you will see a text field. Click on the arrow located at its right and select the name of the peripheral according to how it is named in your /etc/fstab (e.g. "/dev/hdc")

Then click ok

Double click on your new link on the desktop

Et voila, your peripheral will mount.

---

### Post by lerrup on 2005-11-28
TS Eliot, thanks for your tip.

---

### Post by endangst on 2006-01-08
Same problem here, but when I right-click my desktop, the only options it gives are "Create Folder", "Create Launcher", "Create Document", "Clean Up by Name", "Keep Aligned" and "Change Desktop Background".

How can I follow the directions below?  I feel confused.  :confused: (running Ubuntu 5.10)

Thanks!
Endang

> I have the same problem but I have find a workaround:

right click on a free space of the desktop and select

Create new/Link to device/DVD-Rom Device (or Harddisk device, etc.)

write the name of the link in the "General" page (e.g. "pioneer" or "burner", etc.)

click on the Device section:
you will see a text field. Click on the arrow located at its right and select the name of the peripheral according to how it is named in your /etc/fstab (e.g. "/dev/hdc")

Then click ok

Double click on your new link on the desktop

Et voila, your peripheral will mount.

---

### Post by mlomker on 2006-01-08
[QUOTE=endangst](running Ubuntu 5.10)
[/QUOTE]

Are you using Gnome or KDE?  This is the KDE forum and you should have other options if that is what you are running.

---

