---
title: "USB thumb drive errors"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by freesitebuilder on 2007-08-28
My daughter bought herself a Verbatim 1 Gb USB thumb drive this weekend - I  got my old 256Mb one back. :)

She backed up her college work to the new drive - when she looked at the files again, the filenames are all gibberish, special characters rather than letters. The folder names display OK. When we change folders, then they all appear as locked.

Eject asks for admin password, then the icon goes from desktop but we get 
Cannot unmount volume
Cannot remove directory

Properties shows:
> ro nosuid nodev uid=1000 fmask=0077 dmask=0077 codepage=sp437 iocharset=iso8859-1 shortname=mixed utf8
My drive has "rw" rather than "ro" in the properties - so is this new drive set to read-only? (It has no jumper switch like my drive to set to read-only).

Mount shows:
> Mount:
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nCannot unmount volume
Cannot remove directoryosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hdb3 on /home type ext3 (rw)
/dev/hda3 on /media/hda3 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda5 on /media/hda5 type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/STORE'N'GO type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

I tried dmesg:
> dmesg | tail -50
[ 4288.492000] hub 4-1:1.0: USB hub found
[ 4288.496000] hub 4-1:1.0: 4 ports detected
[ 4288.812000] usb 4-1.4: new full speed USB device using uhci_hcd and address 10
[ 4288.940000] usb 4-1.4: configuration #1 chosen from 1 choice
[ 4288.948000] eth1: register 'cdc_ether' at usb-0000:00:11.3-1.4, CDC Ethernet Device, 00:02:8a:19:e4:b7
[ 4304.540000] eth1: no IPv6 routers present
[ 4340.164000] usb 4-1.1: new full speed USB device using uhci_hcd and address 11
[ 4340.264000] usb 4-1.1: not running at top speed; connect to a high speed hub
[ 4340.292000] usb 4-1.1: configuration #1 chosen from 1 choice
[ 4340.296000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 4340.296000] usb-storage: device found at 11
[ 4340.296000] usb-storage: waiting for device to settle before scanning
[ 4345.296000] usb-storage: device scan complete
[ 4345.300000] scsi 5:0:0:0: Direct-Access     Easy     Disk             2.00 PQ: 0 ANSI: 2
[ 4345.412000] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[ 4345.416000] sda: Write Protect is off
[ 4345.416000] sda: Mode Sense: 03 00 00 00
[ 4345.416000] sda: assuming drive cache: write through
[ 4345.428000] SCSI device sda: 512000 512-byte hdwr sectors (262 MB)
[ 4345.428000] sda: Write Protect is off
[ 4345.428000] sda: Mode Sense: 03 00 00 00
[ 4345.428000] sda: assuming drive cache: write through
[ 4345.428000]  sda: unknown partition table
[ 4345.452000] sd 5:0:0:0: Attached scsi removable disk sda
[ 4345.452000] sd 5:0:0:0: Attached scsi generic sg0 type 0
[ 4395.928000] usb 4-1.1: USB disconnect, address 11
[ 4420.664000] psmouse.c: bad data from KBC - bad parity
[ 4421.644000] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 5225.224000] psmouse.c: bad data from KBC - bad parity
[ 5233.008000] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
[ 5275.388000] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
[ 5309.876000] usb 4-1.1: new full speed USB device using uhci_hcd and address 12
[ 5309.976000] usb 4-1.1: not running at top speed; connect to a high speed hub
[ 5310.004000] usb 4-1.1: configuration #1 chosen from 1 choice
[ 5310.008000] scsi6 : SCSI emulation for USB Mass Storage devices
[ 5310.008000] usb-storage: device found at 12
[ 5310.008000] usb-storage: waiting for device to settle before scanning
[ 5315.008000] usb-storage: device scan complete
[ 5315.012000] scsi 6:0:0:0: Direct-Access     Verbatim Store 'n' Go     1.00 PQ: 0 ANSI: 2
[ 5315.016000] SCSI device sda: 1974271 512-byte hdwr sectors (1011 MB)
[ 5315.020000] sda: Write Protect is off
[ 5315.020000] sda: Mode Sense: 00 00 00 00
[ 5315.020000] sda: assuming drive cache: write through
[ 5315.032000] SCSI device sda: 1974271 512-byte hdwr sectors (1011 MB)
[ 5315.032000] sda: Write Protect is off
[ 5315.032000] sda: Mode Sense: 00 00 00 00
[ 5315.032000] sda: assuming drive cache: write through
[ 5315.032000]  sda: sda1
[ 5315.176000] sd 6:0:0:0: Attached scsi removable disk sda
[ 5315.176000] sd 6:0:0:0: Attached scsi generic sg0 type 0

We have similar problems with it in Windows XP, so it's not really an Ubuntu problem, I've emailed Verbatim but I thought I'd get a faster and more Ubuntu-oriented answer here! 

TIA

---

### Post by K.Mandla on 2007-08-28
Just curious: Did you reformat the drive before using it?

If not, was there any funny proprietary software already installed when you started using it? (I got an Imation USB drive once that had some sort of Windows utility already installed on it. It tried to install itself to the first Windows machine I plugged it into. Very irritating.)

---

### Post by tgalati4 on 2007-08-28
I had a cheap emprex flash drive that would work fine on a USB 1.1 port on an older computer, but would get write errors on a new 2.0 port on a powerbook laptop.

Could be the speed of the flash memory.  Some are better than others.  Also, don't pull the stick until the data is completely copied (could take several minutes) don't rely on nautilus or file manager to give you the impression that the data is copied.

After the data is copied:

>fsck /dev/sda1  (or whatever your device is called)

This should keep your drive in RW condition.  If there are errors, the file system will only mount it RO--as a precaution.

Flash drives are like CD burning media.  Some are better than others.  When you find one that works well with your equipment, stick with it.

---

