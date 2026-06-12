---
title: "External CD-drive USB"
date: 2005-03-20
forum: Hardware &amp; Laptops
---

### Post by endless on 2005-03-20
I originally posted my question in the Warty forums, but now I see there are new forums for Hoary, so I will ask my question again. I have an external CDR/RW drive and I would like to mount it. When I boot warty, or knoppix, a new entry in /dev/ named sr0 gets created automatically, which I can use to mount my drive. When I insert the drive in Hoary, only a /dev/sda gets created, and I can't mount from there. I have no clue what the problem could be...

---

### Post by ffnhj on 2005-04-05
Sorry. This is not a solution to this problem.
Actually I have the same problem to you, so I want to share some information about it.
I also have HP cd-writer 8200 series, usb type.
In my case, when I connect it, ubuntu tries to mount it as hard-disk, but fails. It goes into infinite loop. Partial log in dmesg is like this;

--------------------------------------
Additional sense: Not ready to ready change, medium may have changed
sdb : READ CAPACITY failed.
sdb : status=1, message=00, host=0, driver=08
Info fld=0x0, Current sd: sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sdb: test WP failed, assume Write Enabled
sdb: assuming drive cache: write through
 /dev/scsi/host6/bus0/target0/lun0:end_request: I/O error, dev sdb, sector 0
Buffer I/O error on device sdb, logical block 0
Buffer I/O error on device sdb, logical block 0
 unable to read partition table
sdb: Unit Not Ready, sense:
Info fld=0x0, Current : sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sdb : READ CAPACITY failed.
sdb : status=1, message=00, host=0, driver=08
Info fld=0x0, Current sd: sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
s
----------------------------------------------------------

I used this drive normally in Mandrake 10.1, so the hardware is normal.
The first thing I want to know is whether I can stop ubuntu see this drive as hard-disk. Because of the infinite loop, I cannot keep it as plugged in.

I will really apprecirate your help.

---

### Post by endless on 2005-04-06
Well, my problem is not solved (yet), but I don't get your problem either. My dmesg looks like this when I insert the drive:

> usb 1-1: new full speed USB device using ohci_hcd and address 4
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: HP        Model: CD-Writer+ 8200e  Rev: 0001
  Type:   Direct-Access                      ANSI SCSI revision: 00
Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete

In my case the device gets recognized just fine (I think), the problem is that when I insert a cd the medium/partition isn't recognized:

> sudo mount /dev/sda /media/usb-cdrom
mount: No medium found

In your case, do you get the info I get from usb-storage? I mean does it recognize the model of your drive, etcetera? Is the message you posted the entire message after you insert the drive?

Does your drive work in warty or knoppix? When I boot into one of these my drive works perfectly, and this problem has really been driving me crazy for some time now...

---

### Post by jeremy on 2005-04-06
I am getting the same dmesg when I plug in my usb card reader, I have filed a bug at [https://bugzilla.ubuntu.com/show_bug.cgi?id=8585](https://bugzilla.ubuntu.com/show_bug.cgi?id=8585)

---

### Post by endless on 2005-04-06
The difference with my situation seems to be that hal does not crash and remains functional after inserting the drive...

---

### Post by endless on 2005-04-15
Now hoary is official, and it still does not work. The problem is that my drive is recognized, /dev/sda is created automatically when I insert the drive, but the partition on the disc in the drive doesn't get recognized: it says "No Medium found" when I try to mount this drive, even though it works in windows with the same disc. Anybody please has any idea how to resolve this?? Eternal gratitude will be your reward ;-)

---

### Post by OldSpiceAP on 2005-05-16
if it creates the sr0 device when you plug it in you must make sure there is a matching fstab entry for it.  Try this:

first off make a new directory for it to mount to so you can have more than one mounted at a time.

sudo mkdir /media/cdrom1

then edit fstab to show a device like yours:

sudo gedit /etc/fstab

add this line:

/dev/sr0	/media/cdrom1   udf,iso9660 ro,user,noauto  0       0

then save it, and unplug and replug in your usb drive with a cd in it.  It should mount it automagically!  all should now work normally.

also the reason your mount manual mount command didn't work was because you failed to specify a filesystem. It might have worked like

sudo mount -t iso9660 /dev/sr0 /media/cdrom

:)
Good luck!

---

### Post by endless on 2005-05-29
It does not create /dev/sr0, but /dev/sda in hoary. I've followed all of the above steps and I still get 

mount: No medium found

Maybe I should just throw this drive away... it's kinda old anyway. Too bad Ubuntu doesn't recognize the bloody thing.

Maybe someone else knows what's wrong?

---

