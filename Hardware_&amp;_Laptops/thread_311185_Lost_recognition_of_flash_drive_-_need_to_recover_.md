---
title: "Lost recognition of flash drive - need to recover data"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by gray-squirrel on 2006-12-02
I'll try to give as complete an account of what has happened with my flash drive, just in case someone sees I've overlooked something.

I have a Kingston Datatraveler I drive with 1G of space.  It has been working well with KDE until last Friday (Nov. 24, not yesterday).  I did a [FONT="Courier New"]sudo aptitude update[/FONT] and [FONT="Courier New"]sudo aptitude upgrade[/FONT] the day before that.  So, last Friday I when plugged the flash drive in, it was detected, and when I was asked what I wanted to do, I selected "Open in a new window" as I always have done.  From this point on, I get an "An unknown error has occurred" dialog box.  I've had to resort to using the [FONT="Courier New"]pmount [/FONT]command to force the computer to mount the drive, and then I was able to use the drive normally, and even use the "Safely remove" option from Konqueror to unmount the flash drive.

This past Thursday (November 30) there was another problem.  In the morning, I plugged the flash drive in, used [FONT="Courier New"]pmount [/FONT]to get in, and copy a file from my hard disk to the flash drive, then went to "Safely remove" in Konqueror.  Later that day, I plugged it into a Windows XP machine and when I tried to access it, Windows said "Please insert a disk into drive R:".  I wondered whether or not the drive was corrupted, or if there was something else going on.  (Write-caching was not enabled on that machine.)

I got home that night, and could not access anything from it.  In an attempt to do data recovery, I did a [FONT="Courier New"]tail -f /var/log/messages[/FONT] and got the following:

```
Nov 30 21:16:59 localhost kernel: [17701338.408000]     Additional sense: No additional sense information
Nov 30 21:16:59 localhost kernel: [17701338.408000] Info fld=0x0
Nov 30 21:16:59 localhost kernel: [17701338.408000] end_request: I/O error, dev sda, sector 0
Nov 30 21:16:59 localhost kernel: [17701338.472000] sd 5:0:0:0: SCSI error: return code = 0x8000002
Nov 30 21:16:59 localhost kernel: [17701338.472000] sda: Current: sense key: Medium Error
Nov 30 21:16:59 localhost kernel: [17701338.472000]     Additional sense: No additional sense information
Nov 30 21:16:59 localhost kernel: [17701338.472000] Info fld=0x0
Nov 30 21:16:59 localhost kernel: [17701338.472000] end_request: I/O error, dev sda, sector 0
```

Any [FONT="Courier New"]pmount [/FONT]attempt would result in a [FONT="Courier New"]Error: device /dev/sda1 does not exist[/FONT] message.  I took the drive out, and got these messages:


```
Nov 30 22:04:58 localhost kernel: [17704217.520000] usb 5-5: USB disconnect, address 6
Nov 30 22:04:58 localhost kernel: [17704217.528000] sda : READ CAPACITY failed.
Nov 30 22:04:58 localhost kernel: [17704217.528000] sda : status=0, message=00, host=1, driver=00
Nov 30 22:04:58 localhost kernel: [17704217.528000] sda : sense not available.
Nov 30 22:04:58 localhost kernel: [17704217.528000] sda: Write Protect is off
Nov 30 22:04:58 localhost kernel: [17704217.528000] sda : READ CAPACITY failed.
Nov 30 22:04:58 localhost kernel: [17704217.528000] sda : status=0, message=00, host=1, driver=00
Nov 30 22:04:58 localhost kernel: [17704217.528000] sda : sense not available.
Nov 30 22:04:58 localhost kernel: [17704217.528000] sda: Write Protect is off
Nov 30 22:04:58 localhost kernel: [17704217.528000]  sda:<3> 5:0:0:0: rejecting I/O to dead device
Nov 30 22:04:58 localhost kernel: [17704217.528000] printk: 49 messages suppressed.
Nov 30 22:04:58 localhost kernel: [17704217.528000]  unable to read partition table
```


I rebooted, thinking that it may have been a [FONT="Courier New"]hal [/FONT]issue, no luck.  Here's what I got after rebooting and reinserting the flash drive:

```
Nov 30 22:13:13 localhost kernel: [17179793.964000] usb 5-5: new high speed USB device using ehci_hcd and address 3
Nov 30 22:13:14 localhost kernel: [17179794.244000] Initializing USB Mass Storage driver...
Nov 30 22:13:14 localhost kernel: [17179794.244000] scsi2 : SCSI emulation for USB Mass Storage devices
Nov 30 22:13:14 localhost kernel: [17179794.248000] usbcore: registered new driver usb-storage
Nov 30 22:13:14 localhost kernel: [17179794.248000] USB Mass Storage support registered.
Nov 30 22:13:19 localhost kernel: [17179799.252000]   Vendor: Kingston  Model: DataTraveler 2.0  Rev: 1.00
Nov 30 22:13:19 localhost kernel: [17179799.252000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Nov 30 22:13:19 localhost kernel: [17179799.300000] Driver 'sd' needs updating - please use bus_type methods
Nov 30 22:13:19 localhost kernel: [17179799.308000] SCSI device sda: 1971200 512-byte hdwr sectors (1009 MB)
Nov 30 22:13:19 localhost kernel: [17179799.308000] sda: Write Protect is off
Nov 30 22:13:19 localhost kernel: [17179799.320000] SCSI device sda: 1971200 512-byte hdwr sectors (1009 MB)
Nov 30 22:13:19 localhost kernel: [17179799.324000] sda: Write Protect is off
Nov 30 22:13:19 localhost kernel: [17179799.324000]  sda:<6>sd 2:0:0:0: SCSI error: return code = 0x8000002
Nov 30 22:13:19 localhost kernel: [17179799.392000] sda: Current: sense key: Medium Error
Nov 30 22:13:19 localhost kernel: [17179799.392000]     Additional sense: No additional sense information
Nov 30 22:13:19 localhost kernel: [17179799.392000] Info fld=0x0
Nov 30 22:13:19 localhost kernel: [17179799.392000] end_request: I/O error, dev sda, sector 0
Nov 30 22:13:19 localhost kernel: [17179799.452000] sd 2:0:0:0: SCSI error: return code = 0x8000002
Nov 30 22:13:19 localhost kernel: [17179799.452000] sda: Current: sense key: Medium Error
Nov 30 22:13:19 localhost kernel: [17179799.452000]     Additional sense: No additional sense information
Nov 30 22:13:19 localhost kernel: [17179799.452000] Info fld=0x0
Nov 30 22:13:19 localhost kernel: [17179799.452000] end_request: I/O error, dev sda, sector 0
Nov 30 22:13:19 localhost kernel: [17179799.456000]  unable to read partition table
Nov 30 22:13:19 localhost kernel: [17179799.456000] sd 2:0:0:0: Attached scsi removable disk sda
Nov 30 22:13:19 localhost kernel: [17179799.472000] sd 2:0:0:0: Attached scsi generic sg0 type 0
Nov 30 22:13:19 localhost kernel: [17179799.536000] sd 2:0:0:0: SCSI error: return code = 0x8000002
Nov 30 22:13:19 localhost kernel: [17179799.536000] sda: Current: sense key: Medium Error
Nov 30 22:13:19 localhost kernel: [17179799.536000]     Additional sense: No additional sense information
Nov 30 22:13:19 localhost kernel: [17179799.536000] Info fld=0x0
Nov 30 22:13:19 localhost kernel: [17179799.536000] end_request: I/O error, dev sda, sector 0
Nov 30 22:13:19 localhost kernel: [17179799.596000] sd 2:0:0:0: SCSI error: return code = 0x8000002
Nov 30 22:13:19 localhost kernel: [17179799.596000] sda: Current: sense key: Medium Error
Nov 30 22:13:19 localhost kernel: [17179799.596000]     Additional sense: No additional sense information
Nov 30 22:13:19 localhost kernel: [17179799.596000] Info fld=0x0
Nov 30 22:13:19 localhost kernel: [17179799.596000] end_request: I/O error, dev sda, sector 8
Nov 30 22:13:19 localhost kernel: [17179799.660000] sd 2:0:0:0: SCSI error: return code = 0x8000002
Nov 30 22:13:19 localhost kernel: [17179799.660000] sda: Current: sense key: Medium Error
Nov 30 22:13:19 localhost kernel: [17179799.660000]     Additional sense: No additional sense information
Nov 30 22:13:19 localhost kernel: [17179799.660000] Info fld=0x0
Nov 30 22:13:19 localhost kernel: [17179799.660000] end_request: I/O error, dev sda, sector 16
```

(The same error would repeat for several more sectors, which are all multiples of 8.)

What is meant by "Driver 'sd' needs updating"?

I tested my Creative MuVo flash drive this morning, and it works fine still.  But, I used the [FONT="Courier New"]pumount [/FONT]command to unmount that, and that was something I didn't know about until last night.

In the meantime, is there a reason for all this, and more importantly, is there a way I can force KDE to recognize the drive in a way where I can at least run a [FONT="Courier New"]dd [/FONT]command and recover as much as possible?

---

### Post by gray-squirrel on 2006-12-04
An update. . .

I came across [one page]("http://aemes.mae.ufl.edu/~vql/linux/flash.drive.html") dealing with flash drives, and another about the [kernel not reading the partition table]("http://lkml.org/lkml/2005/7/5/4") of a flash drive.  I was hoping that Kubuntu would at least recognize the drive fully.

Apparently, the kernel does know my flash drive is attached:

```
$ cd /proc/scsi
/proc/scsi $ ls
device_info  sata_via  scsi  sg  usb-storage
/proc/scsi $ cat usb-storage
cat: usb-storage: Is a directory
/proc/scsi $ ls usb-storage
8
/proc/scsi $ cat usb-storage/8
   Host scsi8: usb-storage
       Vendor: Kingston
      Product: DataTraveler 2.0
Serial Number: 0605042142230
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:
```


But, it still refuses to look for the partition table:

```
$ fdisk /dev/sda

Unable to read /dev/sda
$ sudo fdisk /dev/sda
Password:

Unable to read /dev/sda

```

I guess I will need a low-level tool to get at the files on the flash drive.  There was an important document on there which I created and save on that drive that I intended to save to my hard disk when I got home but never got to doing due to the problem I mentioned earlier.  If anyone has suggestions on what I could use to recover data which does not require that /dev/sda1 be created (which is what would have happened if the partition table could be read), please let me know.  Thanks.

---

### Post by la3875 on 2006-12-09
KDE/Kubuntu wont recognize my Kingston "key" or the USB connection to my digital camera even though I have loaded digikam. Frustratingly when I open a new session in Gnome all are recognized and happily accessed. Can't someone come up with a fix for this quirk in KDE/Kubuntu? Please, please please...

---

### Post by Matt Yun on 2006-12-09
You should try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"); just do 'apt-get install testdisk'.  Testdisk is actually a collection of utilities to do partition and file recovery.

I've only used this program suite once to recover deleted files from a FAT32 partition, so I can't give you much guidance.  However, you should be able to  find documentation at that site.

---

### Post by gray-squirrel on 2006-12-10
> **Matt Yun said:**
> You should try [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"); just do 'apt-get install testdisk'.  Testdisk is actually a collection of utilities to do partition and file recovery.

I've only used this program suite once to recover deleted files from a FAT32 partition, so I can't give you much guidance.  However, you should be able to  find documentation at that site.

Thanks.  I have just tried out TestDisk a few minutes ago, and it couldn't find any partitions.  I did get a ton of read errors, though.  It also reported this on start up:

```
Disk /dev/sda - 962 MB - CHS 962 64 32, sector size=512
```

Over the past two days I also tried imaging the drive using GNU ddrescue, both using /dev/sda and /dev/raw/raw1 (a raw device I set up).  I could not recover anything either way.

If I could only understand how a mounting/unmounting operation could make a flash drive unusable like this. . . it would have been understandable if a boot sector or the partition table were messed up and nothing else.

Windows recognizes this same flash drive as being plugged, but depending on the program, it is either treated as an unformatted removable disk or a nonexistent device.

There is one last thing I'm considering trying, but I want to get second opinions on this first.  If I were to do a quick format on this, and do nothing else, I should be able to recover something.  It may be the only thing which would remove the read errors.  Is it recommended to do the quick format in Kubuntu or Windows?  I have no problem doing this on a Windows box, but if it is safe to do it within Kubuntu, I can get this done and try to image the drive again, followed by tests with [Foremost]("http://foremost.sourceforge.net/"), [Scalpel]("http://www.digitalforensicssolutions.com/Scalpel/"), or [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

---

