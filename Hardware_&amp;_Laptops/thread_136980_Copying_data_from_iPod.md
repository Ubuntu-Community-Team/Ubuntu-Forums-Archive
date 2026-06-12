---
title: "Copying data from iPod"
date: 2006-02-27
forum: Hardware &amp; Laptops
---

### Post by Plexxxy on 2006-02-27
A couple months ago I finally committed to making the switch from Windows to linux after giving Ubuntu a shot. It's been a rather smooth affair (had some prior linux experience), except in the iPod department. I can mount and transfer music *to* my g4/20GB iPod using gtkpod, but not *from* it. Gtkpod begins to read whatever I've selected to be read from the device, but it only gets a few MB into the transfer before it chokes.

It's not just with gtkpod either. This happens even when dumping random files on it through nautilus or the command line. Here's the output from dmesg:
```

[4311205.792000] usb 4-4: new high speed USB device using ehci_hcd and address 4[4311205.869000] scsi1 : SCSI emulation for USB Mass Storage devices
[4311205.870000] usb-storage: device found at 4
[4311205.870000] usb-storage: waiting for device to settle before scanning
[4311210.870000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4311210.870000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4311210.874000] SCSI device sda: 39063023 512-byte hdwr sectors (20000 MB)
[4311210.874000] sda: Write Protect is off
[4311210.874000] sda: Mode Sense: 64 00 00 08
[4311210.874000] sda: assuming drive cache: write through
[4311210.878000] SCSI device sda: 39063023 512-byte hdwr sectors (20000 MB)
[4311210.879000] sda: Write Protect is off
[4311210.879000] sda: Mode Sense: 64 00 00 08
[4311210.879000] sda: assuming drive cache: write through
[4311210.879000]  /dev/scsi/host1/bus0/target0/lun0: p1 p2
[4311210.945000] Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
[4311210.947000] usb-storage: device scan complete
[4311356.968000] usb 4-4: reset high speed USB device using ehci_hcd and address 4
[4311373.155000] scsi: Device offlined - not ready after error recovery: host 1 channel 0 id 0 lun 0
[4311373.155000] SCSI error : <1 0 0 0> return code = 0x50000
[4311373.155000] end_request: I/O error, dev sda, sector 692493
[4311373.155000] Buffer I/O error on device sda2, logical block 612168
[4311373.155000] scsi1 (0:0): rejecting I/O to offline device
[4311373.155000] Buffer I/O error on device sda2, logical block 612169
[4311373.155000] Buffer I/O error on device sda2, logical block 612170
[4311373.155000] Buffer I/O error on device sda2, logical block 612171
[4311373.155000] Buffer I/O error on device sda2, logical block 612172
[4311373.155000] Buffer I/O error on device sda2, logical block 612173
[4311373.155000] Buffer I/O error on device sda2, logical block 612174
[4311373.155000] Buffer I/O error on device sda2, logical block 612175
[4311373.155000] Buffer I/O error on device sda2, logical block 612176
[4311373.155000] Buffer I/O error on device sda2, logical block 612177
[4311373.155000] scsi1 (0:0): rejecting I/O to offline device
[4311373.155000] scsi1 (0:0): rejecting I/O to offline device
[4311373.155000] scsi1 (0:0): rejecting I/O to offline device
[4311373.155000] scsi1 (0:0): rejecting I/O to offline device
[4311373.155000] scsi1 (0:0): rejecting I/O to offline device
[4311373.155000] scsi1 (0:0): rejecting I/O to offline device
[4311373.161000] scsi1 (0:0): rejecting I/O to offline device

```

I've tried switching to the -k7 kernel from the default 386 (running an Athlon XP here) as well as completely formatting the device with no luck. Even tried different usb ports. I think it's something goofy going on with usb, but I'm stumped on the specifics.

Suggestions, please? This is one of the few issues that's forcing me to keep a Windows installation :cry:

---

### Post by KingOfNowhere on 2006-02-27
Plexxxy,

im not sure why gtkpod would choke during ipod->desktop transfer (possibly has something todo with you I/O errors on your usb bus)

However, the music on your ipod is simply stored as either mp3 files or aac files. The music can typically be found on the ipod's data partition in /iPod_Control/Music/ (for windows ipods).

In that folder you will find alot of obsurely named .mp3 files in various directories, that is all your music. They are not named correctly, but all you need for that is an ID3 tag editor (such as Cantus) to read the tags of your music and rename them. So if gtkpod won't transfer your music, you can do it manually, but u will have to rename them yourself. 

You can also try Amarok, they have improving ipod support.

Also, for reference, you may want to check out my [guide]("http://ubuntuforums.org/showthread.php?t=103071")

Hope that helped,

-KingOfNowhere

---

### Post by Plexxxy on 2006-02-27
Thanks for your reply. Yep, tried simply copying through nautilus; looks like the file begins to transfer, but hangs a few seconds in. Then I hear the "click" of the hdd parking in the iPod (offlined).

[[IMG]http://img390.imageshack.us/img390/3157/ipodfilecopy7cs.png[/IMG]](http://imageshack.us)

I followed your guide about a week ago, thinking I was doing something wrong in mounting it. But seeing as I can send music & files to the device and read/write the ituned db without any problems (although that may be because the db is not very large), I'm somewhat convinced this is more a usb issue than an ipod one. I think I'll try copying some files with usb 1.1 and see if it anything changes.

Thanks again for your reply :)

---

