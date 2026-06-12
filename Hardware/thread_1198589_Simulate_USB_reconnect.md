---
title: "Simulate USB reconnect?"
date: 2009-06-27
forum: Hardware
---

### Post by *uu on 2009-06-27
Hi people,

I'm currently programming an application that is supposed to re-partition external harddrives (USB and hopefully eSATA) and create a filesystem on the drives. I currently use the linux-built-in tools parted (mktable and mkpart) and mkfs.* to do this, and built a nice GUI where the user can do some selections like desired filesystem.

Now, when a drive was originally formatted with NTFS filesystem, and the application re-partitions it and creates an EXT3 filesystem on the drive (or vice versa), this all works fine, but the device can normally only be mounted afterwards, when it is physically dis- and reconnected to the USB port. When trying to remount the newly created filesystem (via nautilus, via 'gnome-mount -d /dev/sde1' or even via the corresponding 'dbus-send' command) without physical reconnect, I get some error message like this:
```
Error org.freedesktop.Hal.Device.Volume.UnknownFailure: 
NTFS signature is missing. Failed to mount '/dev/sdf1': 
Invalid argument The device '/dev/sdf1' doesn't seem to 
have a valid NTFS. Maybe the wrong device is used? Or 
the whole disk instead of a partition (e.g. /dev/sda, 
not /dev/sda1)? Or the other way around? 
ERROR: dbus-send failed
```
...or similarly, when filesystem was changed from NTFS to EXT3:
```
Error org.freedesktop.Hal.Device.Volume.UnknownFailure: 
mount: wrong fs type, bad option, bad superblock on /dev/sdf1,        
missing codepage or helper program, or other error        
In some cases useful info is found in syslog - try        
dmesg | tail  or so  
ERROR: dbus-send failed

```
...which is normal, I guess, as apparently, the old filesystem info is still saved in some sort of cache associated with HAL. Sometimes it workes, when specifying a filesystem with the gnome-mount command, apparently mostly when the new FS is EXT3 (not sure yet if this would always work). But especially when the new FS is NTFS and I run 'gnome-mount -d /dev/sde1 -f ntfs-3g', I only get this message:
```
Cannot get volume.fstype.alternative
```
So far, I couldn't find an automagic mount command (which would invoke all the HAL/DBUS magic like automatic mount point creation, appearance of the drive icons in the file managers and on the desktop, ...) to mount this newly created NTFS filesystem -- and possibly sporadically also a new EXT3 FS -- without unplugging and replugging the device.

Is there a possibility to, say, simulate a physical dis- and reconnect of a USB drive to make HAL do all its magic from a fresh start? Or can anyone give me a hint where HAL would save this old filesystem information? Or am I going about this completely the wrong way?

Any pointer in the right direction is appreciated. :-)

Regards,
*uu

---

