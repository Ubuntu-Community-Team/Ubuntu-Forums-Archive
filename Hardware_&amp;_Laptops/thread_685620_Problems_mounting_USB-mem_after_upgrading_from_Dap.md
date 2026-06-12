---
title: "Problems mounting USB-mem after upgrading from Dapper to Gutsy"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by toyohta on 2008-02-02
I just upgraded Ubuntu (one version at a time) from Dapper to Gutsy.

Now I can no longer mount my USB memory stick or my external hard drive (also USB).

In Dapper, when I plugged these in, Dapper would automatically mount them, and they were immediately available.

Gutsy also attempts to mount them, but gives the following error message:
    Cannot mount volume. Unable to mount the volume 'UDISK 2.0'.

When I expand the details, it says:
    mount: wrong fs type, bad option, bad superblock on /dev/sda1, 
    missing codepage or helper program, or other error
    In some cases useful info is found in syslog
      - try dmesg | tail or so

When I run "dmesg | tail", I get the following information:
    [17182335.568000] sda: assuming drive cache: write through
    [17182335.572000] SCSI device sda: 3851776 512-byte hdwr sectors (1972 MB)
    [17182335.572000] sda: Write Protect is off
    [17182335.572000] sda: Mode Sense: 23 00 00 00
    [17182335.572000] sda: assuming drive cache: write through
    [17182335.572000]  sda: sda1
    [17182335.572000] sd 3:0:0:0: Attached scsi removable disk sda
    [17182335.572000] sd 3:0:0:0: Attached scsi generic sg0 type 0
    [17182335.576000] usb-storage: device scan complete
    [17182336.064000] FAT: Unrecognized mount option "usefree" or missing value 

Can anyone tell me how to handle this? Do I need to mount the drives manually, and do I need to use any special options? I don't know what "usefree" does (found nothing on the "mount" man page), and so I really have no idea why this is going wrong.

---

### Post by toyohta on 2008-02-03
I never found out what "usefree" does, or why linux tried to automatically mount the devices in the first place.

However, I did figure out how to mount the devices, so in case anyone else (inexperienced, like myself) stryggle with this, I managade to manually mount the devices and afterwards learned to automate this.

I first made three new directories (I chose to let the directory names of the mount points match the names of the device files):
  sudo mkdir /media/sda1
  sudo mkdir /media/sdb1
  sudo mkdir /media/sdc1

I then manually mounted my USB devices (I have 3) with:
   sudo mount -t vfat /dev/sda1 /media/sda1/
   sudo mount -t vfat /dev/sdb1 /media/sda2/
   sudo mount -t vfat /dev/sdc1 /media/sda3/

This was, fine, but I still had to manually mount and unmount the external devices. I added the following lines to fstab:
  /dev/sda1 /media/sda1 vfat users,rw,noauto 0 0
  /dev/sdb1 /media/sdb1 vfat users,rw,noauto 0 0
  /dev/sdc1 /media/sdc1 vfat users,rw,noauto 0 0

With this configuration, the devices mount automatically, so this works pretty well.

However, I still have to unmount the devices manually. If I unplug a device and then plug it in again, I get the same old error message, probably because I haven't set up any more mount points. If I unmount the device and then reconnect it, it mounts fine.

Is there a way of having the devices unmount automatically as I unplug them. This would be ultimately convenient.

---

