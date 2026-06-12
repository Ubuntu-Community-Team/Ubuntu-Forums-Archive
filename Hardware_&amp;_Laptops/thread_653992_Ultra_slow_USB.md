---
title: "Ultra slow USB"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by hidarikani on 2007-12-30
Writing 100MB to my USB Flash drive on Xubuntu 7.4 takes 8 minutes.
On Win XP it takes a couple of seconds.

I've tried to mount it manually:
```
sudo mount /dev/sdb1 /media/flash-drive -o umask=000,sync
```
async or sync it's ultra slow

Please help.

---

### Post by OoooMatron on 2008-01-06
I am also looking for a solution to this. It takes a long long time to copy files to my USB stick which works much more swiftly in XP:

I am sure that the USB was never this slow before and it's a problem that has happened in the last couple of months.

---

### Post by reppekjeks on 2008-01-19
I also have the same problem. Writing 700MB to my Twinmos M9 4GB memory stick takes 10-12 minutes, but only 2 minutes in windows xp. I wonder if it is recognized only as a USB 1.1 device since the transfer rate is just about 1MB/s?

---

### Post by maxino on 2008-01-20
Judging from the large number of similar (mostly unanswered) posts that keep popping up in every distro-forum (Ubuntu, Mandriva, Gentoo, Suse, etc) I suspect that there is a problem in the current kernel/module handling the USB2.0.
On the very same PC I have got a memory stick which works flawlessly and a external 80GB hd which literally crawls freezing the PC from time to time... and no googling the entire 'net helped a bit.
It would be nice to hear from someone involved in the development.

For the time being, not even usbview works ("cannot open the file /proc/bus/usb/devices") which would otherwise be a helpful tool (as far as I know this is a confirmed bug).

Sorry for not being able to offer any help, I am in the same situation (together with countless others)...

---

### Post by hidarikani on 2008-01-21
Looks like i'm not alone.
I used to backup files to my usb drive on XP but I can't do that on Ubuntu,
so I've tried to write my files to a CD-RW and guess what?
Ubuntu locks every time I insert a blank CD-RW and launch Brasero.
I'm not going to use an OS that makes everyday tasks impossible.

---

### Post by erginemr on 2008-01-21
> **hidarikani said:**
> Looks like i'm not alone.
I used to backup files to my usb drive on XP but I can't do that on Ubuntu,
so I've tried to write my files to a CD-RW and guess what?
Ubuntu locks every time I insert a blank CD-RW and launch Brasero.
I'm not going to use an OS that makes everyday tasks impossible.

Does it happen with other CD burning apps, too?
Please try another nice app: 
GnomeBaker or K3b 

before giving up on Ubuntu.

---

### Post by LastChanceLeeward on 2008-01-21
I too have noticed USB is not that quick. Just bought an external firewire hdd because my friend tells me it bothers the cpu(s) less and has good throughput. Only wish my HP had firewire 800 (1394b) and not plain jane firewire 400 (1394). I realize that just going towards firewire is not the solution for my usb stick, however, and it is SLOWWWWW.

---

### Post by hidarikani on 2008-01-21
I drag and drop a 100MB folder to the flash drive.
Then the 'Copying Files...' window appears and it takes a minute for it to reach 100%.
After that I right click the drive and select 'Unmount'
Finally 'Writing data to device' baloon appears, and stays for 8 minutes.

After inserting usb drive:
```

[ 2804.306881] usb 3-1: new full speed USB device using uhci_hcd and address 7
[ 2804.481873] usb 3-1: configuration #1 chosen from 1 choice
[ 2804.534908] scsi9 : SCSI emulation for USB Mass Storage devices
[ 2804.536124] usb-storage: device found at 7
[ 2804.536131] usb-storage: waiting for device to settle before scanning
[ 2809.535531] usb-storage: device scan complete
[ 2809.538533] scsi 9:0:0:0: Direct-Access              USB FLASH DRIVE  34CH PQ: 0 ANSI: 0 CCS
[ 2810.664014] sd 9:0:0:0: [sdb] 1007616 512-byte hardware sectors (516 MB)
[ 2810.668014] sd 9:0:0:0: [sdb] Write Protect is off
[ 2810.668020] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 2810.668023] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 2810.680018] sd 9:0:0:0: [sdb] 1007616 512-byte hardware sectors (516 MB)
[ 2810.682997] sd 9:0:0:0: [sdb] Write Protect is off
[ 2810.683003] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 2810.683006] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 2810.683010]  sdb: sdb1
[ 2810.689090] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 2810.689145] sd 9:0:0:0: Attached scsi generic sg1 type 0

```

This doesn't help:
```
sudo rmmod ehci_hcd
```

---

### Post by Burillo on 2008-02-29
try unplug, then "sudo rmmod uhci_hcd" and plug in

---

