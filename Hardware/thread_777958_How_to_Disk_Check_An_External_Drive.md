---
title: "How to Disk Check An External Drive"
date: 2008-05-01
forum: Hardware
---

### Post by Anxiety35 on 2008-05-01
I was recently backing up a large amount of files from my laptop onto my external when something went wrong. For some reason in the middle, it unmounted and now has been giving me problems ever sense.

Often times it just doesn't mount (it gives no error message). I suspect there is either some corruption or some bad sectors causing this problem but I don't know how to scan an external drive from ubuntu and haven't been able to find any help from searching around.

Would fsck be able to do this? If so what would the command be?
If it's needed, I'm running 8.04.

---

### Post by bluetoad on 2008-05-01
Have a look in /var/log/messages for error messages etc
You should also see what the device is in /var/log/messages


cat /proc/partitions

will show all of your curent partitions

the df command will show the currently mounted partitions
swapon -s 
will show the current swap partitions

So armed with the above you should be able to work which partition(s) is/are on your external drive.

You will need to make sure the partitions are unmounted before running fsck (df).  Try to do that through the
file manager (icon on desktop or Place in the Gnome menu).  To use the command line to unmount /dev/sdc1 for example

sudo umount /dev/sdc1

Then depending on the type of the filesystem you can run, for example for ext3, 

sudo fsck.ext3 /dev/sdc1


See 'man fsck' for more options

---

### Post by Anxiety35 on 2008-05-01
Thanks, it shows up in the partitions list, but not in the mounted ones.

I'm going to try and fsck it now. It's going to take forever though since It's a Terabyte.

I'll post the results, thanks for the help.

Also, this is what is put in that log file when I plug in the drive (Which has 2 partitions):
> 
May  1 16:59:34 william-laptop kernel: [11711.452181] usb 5-1: new high speed USB device using ehci_hcd and address 18
May  1 16:59:35 william-laptop kernel: [11711.587284] usb 5-1: configuration #1 chosen from 1 choice
May  1 16:59:35 william-laptop kernel: [11711.588255] scsi3 : SCSI emulation for USB Mass Storage devices
May  1 16:59:40 william-laptop kernel: [11718.638058] scsi 3:0:0:0: Direct-Access     WDC WD50 00AAJS-22TKA0         PQ: 0 ANSI: 2 CCS
May  1 16:59:40 william-laptop kernel: [11718.639650] sd 3:0:0:0: [sdb] 1953546336 512-byte hardware sectors (1000216 MB)
May  1 16:59:40 william-laptop kernel: [11718.640384] sd 3:0:0:0: [sdb] Write Protect is off
May  1 16:59:40 william-laptop kernel: [11718.641759] sd 3:0:0:0: [sdb] 1953546336 512-byte hardware sectors (1000216 MB)
May  1 16:59:40 william-laptop kernel: [11718.642508] sd 3:0:0:0: [sdb] Write Protect is off
May  1 16:59:40 william-laptop kernel: [11718.642525]  sdb: sdb1 sdb2
May  1 16:59:40 william-laptop kernel: [11718.645219] sd 3:0:0:0: [sdb] Attached SCSI disk
May  1 16:59:40 william-laptop kernel: [11718.645287] sd 3:0:0:0: Attached scsi generic sg2 type 0


---

### Post by Anxiety35 on 2008-05-01
I tried ext3 and ext2 because I'm not sure what kind it is. How do I check?

Also this is the message I get when trying:
fsck.ext3(or 2) /dev/sdb

> 
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Edit:
I tried this also since the above message suggested it

> 
william@william-laptop:~$ sudo e2fsck -b 8193 /dev/sdb
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sdb
Filesystem mounted or opened exclusively by another program?


---

### Post by bluetoad on 2008-05-01
sudo fsck -N /dev/sdc1
[sudo] password for peter:
fsck 1.40.2 (12-Jul-2007)
[/sbin/fsck.ext3 (1) -- /dev/sdc1] fsck.ext3 /dev/sdc1 

The -N doesn't actually so the check.  Just shows what it will do

---

### Post by Anxiety35 on 2008-05-01
Alright, that told me it was ext2, So this is what happened.

> 
william@william-laptop:~$ sudo fsck.ext2 /dev/sdb
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


---

### Post by argosreality on 2008-05-01
> **Anxiety35 said:**
> Alright, that told me it was ext2, So this is what happened.Did you format this external drive as ext2/3? Unless you explicitly formated it as such then its most likely going to be an NTFS formated drive which would explain the constant error messages you're getting when attempting to fsck it.

Also, were you seeing a bunch of disconnect and reset messages in your logs during/after the drive disconnected? 

I had the same issue of a drive bombing on me in the middle of a transfer and now its not even staying connected if I hit it with anything (traffic, browsing it, etc.) but the drives passed health checks connected to a windows pc. 

This is what I was seeing: 

```
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.338777] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_6AE86A25E869EFAD'). 
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.339581] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Seagate_FreeAgentDesktop_6QF21118_0_0'). 
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.339807] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________6QF21118_if0_scsi_host_scsi_device_lun0'). 
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.341133] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________6QF21118_if0_scsi_host'). 
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.344557] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________6QF21118_if0'). 
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.344681] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________6QF21118'). 
May  1 20:31:59 mars kernel: [  440.192630] usb 6-4: new high speed USB device using ehci_hcd and address 7
May  1 20:32:14 mars kernel: [  449.166568] usb 6-4: device descriptor read/64, error -110
May  1 20:32:29 mars kernel: [  457.069534] usb 6-4: device descriptor read/64, error -110
May  1 20:32:29 mars kernel: [  457.172002] usb 6-4: new high speed USB device using ehci_hcd and address 8
May  1 20:32:45 mars kernel: [  468.601550] usb 6-4: device descriptor read/64, error -110
May  1 20:33:00 mars kernel: [  475.996408] usb 6-4: device descriptor read/64, error -110
May  1 20:33:00 mars kernel: [  476.099840] usb 6-4: new high speed USB device using ehci_hcd and address 9
May  1 20:33:11 mars kernel: [  481.059507] usb 6-4: device not accepting address 9, error -110
May  1 20:33:11 mars kernel: [  481.112776] usb 6-4: new high speed USB device using ehci_hcd and address 10
```

---

### Post by Anxiety35 on 2008-05-01
I didn't format it as ext2/3. It is NTSF, I guess I just thought etc2 because that's the message that came up.

As for the messages when I disconnect it, right now it's not mounting (Although it does show up in my "places" menu) so when I turn it off, and unplug it, it just says:

> 
May  1 18:17:15 william-laptop kernel: [16368.675405] usb 5-3: USB disconnect, address 27
May  1 18:22:43 william-laptop kernel: [16696.644460] usb 5-5.1: USB disconnect, address 29
May  1 18:22:43 william-laptop kernel: [16696.644629] usblp0: removed
May  1 18:22:43 william-laptop kernel: [16696.644777] usb 5-5.3: USB disconnect, address 30
May  1 18:22:43 william-laptop kernel: [16699.475235] usb 5-5: reset high speed USB device using ehci_hcd and address 28
May  1 18:22:45 william-laptop kernel: [16700.686486] usb 5-5: reset high speed USB device using ehci_hcd and address 28
May  1 18:22:45 william-laptop kernel: [16700.846390] usb 5-5: USB disconnect, address 28
May  1 18:22:45 william-laptop kernel: [16700.958331] usb 5-5: new high speed USB device using ehci_hcd and address 31
May  1 18:22:47 william-laptop kernel: [16700.784625] usb 5-5: new high speed USB device using ehci_hcd and address 32
May  1 18:22:49 william-laptop kernel: [16702.664463] usb 5-5: new high speed USB device using ehci_hcd and address 33
May  1 18:22:49 william-laptop kernel: [16703.183165] usb 5-5: new high speed USB device using ehci_hcd and address 34


---

### Post by Anxiety35 on 2008-05-01
So if it's NTFS, how do I disk check it? Because sudo fsck.ntfs /dev/sdb doesn't do it.

---

### Post by argosreality on 2008-05-02
> **Anxiety35 said:**
> So if it's NTFS, how do I disk check it? Because sudo fsck.ntfs /dev/sdb doesn't do it.there's ntfsfix but it's not as thorough as chkdsk. Basically just checks for some basic inconsitences and rebuilds the journal 

You might need to download a copy of Ultimate Boot CD which has some NTFS diagnostic utilites or if you have a windows disk laying around you can force a check on it through the recovery console.

However, it looks like you're having the same drive issue as I am which in my case WASN'T a bad drive. Its something to do with Hardy's handling of USB drives

---

### Post by Anxiety35 on 2008-05-02
You're right, it does sound similar to yours. I can deal with it for now if there isn't a fix. It is strange how it started randomly though.

I was just a little paranoid about losing so much data.

---

### Post by Anxiety35 on 2008-05-04
Alright, so I'm going to see if I can get a little more help here.

It always mounts the first time after I've booted up, but once I unmount it it won't mount again. I've seen elsewhere suggestions to check the mount point, but I don't know how to do this.

Also, the drive doesn't show up in my fstab file (as of now when I'm trying to mount it a second time anyways).

---

