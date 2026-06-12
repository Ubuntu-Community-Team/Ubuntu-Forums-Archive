---
title: "Usb"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by heyjoe on 2006-03-11
Hi there. I was wanting some instruction on how to mount a 128mb usb flash drive. Breezy Badger doesn't seem to be reocgnizing it.

When i plug it in and type mount in terminal, i get: 

frank@ubuntu:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
frank@ubuntu:~$

Secondly, less importantly, breezy is recognizing my mp3 player, but i get an error message whenever i unmount it. any help would be much appreciated.

thanks in advance, 

frank

P.S.- I am very new to linux and not very good at the command line. so detailed help would be much appreciated.

---

### Post by Lucho on 2006-03-11
I'm still a noob, even after ayear of easy distros like kurumin and
ubuntu, so don't feel bad ;) 
   Maybe it will help, maybe not, but if you're using KDE try this: 
after plugging in the flash drive, instead of going to a terminal
open Konqueror. You should be at the starting point page; go to
storage media, and your flash drive should be right alongside
the floppy drive and HDD. From there just click to mount.
  At least that's how it's *supposed* work in  breezy

---

### Post by heyjoe on 2006-03-11
OK, to clarify the problem: sometimes the usb device is recognized and sometimes it isn't (usually not recognized) and i am confident that i know how to look for it. when it didnt work i got this in terminal following a tail -f /var/log/messages :

frank@ubuntu:~$ tail -f /var/log/messages
Mar 12 10:19:21 localhost kernel: [4369138.034000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 2254
Mar 12 10:19:21 localhost kernel: [4369138.034000]   Type:   Direct-Access                 ANSI SCSI revision: 00
Mar 12 10:19:21 localhost kernel: [4369138.037000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
Mar 12 10:19:21 localhost kernel: [4369138.039000] sda: Write Protect is off
Mar 12 10:19:21 localhost kernel: [4369138.042000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
Mar 12 10:19:21 localhost kernel: [4369138.043000] sda: Write Protect is off
Mar 12 10:19:21 localhost kernel: [4369138.043000]  /dev/scsi/host7/bus0/target0/lun0: unknown partition table
Mar 12 10:19:21 localhost kernel: [4369138.046000] Attached scsi removable disk sda at scsi7, channel 0, id 0, lun 0
Mar 12 10:19:21 localhost scsi.agent[30069]:      sd_mod: loaded sucessfully (for disk)
Mar 12 10:19:52 localhost kernel: [4369169.073000] usb 4-4: USB disconnect, address 8
Mar 12 10:22:49 localhost kernel: [4369346.239000] usb 4-4: new high speed USB device using ehci_hcd and address 9
Mar 12 10:22:49 localhost kernel: [4369346.527000] scsi8 : SCSI emulation for USB Mass Storage devices
Mar 12 10:22:49 localhost usb.agent[30275]:      usb-storage: already loaded
Mar 12 10:22:54 localhost kernel: [4369351.529000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 2254
Mar 12 10:22:54 localhost kernel: [4369351.529000]   Type:   Direct-Access                 ANSI SCSI revision: 00
Mar 12 10:22:54 localhost kernel: [4369351.533000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
Mar 12 10:23:07 localhost scsi.agent[30321]: Attribute /sys/devices/pci0000:00/0000:00:03.3/usb4/4-4/4-4:1.0/host8/target8:0:0/8:0:0:0/type does not exist
Mar 12 10:24:26 localhost kernel: [4369443.616000] usb 4-4: reset high speed USB device using ehci_hcd and address 9
Mar 12 10:24:33 localhost kernel: [4369449.695000] sda: Write Protect is off
Mar 12 10:25:53 localhost kernel: [4369529.765000] usb 4-4: reset high speed USB device using ehci_hcd and address 9
Mar 12 10:25:53 localhost kernel: [4369529.844000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
Mar 12 10:27:25 localhost kernel: [4369621.917000] usb 4-4: reset high speed USB device using ehci_hcd and address 9
Mar 12 10:27:31 localhost kernel: [4369627.997000] sda: Write Protect is off
Mar 12 10:28:45 localhost kernel: [4369627.997000]  /dev/scsi/host8/bus0/target0/lun0:<6>usb 4-4: reset high speed USB device using ehci_hcd and address 9
Mar 12 10:28:45 localhost kernel: [4369702.143000]  unknown partition table
Mar 12 10:28:45 localhost kernel: [4369702.143000] Attached scsi removable disk sda at scsi8, channel 0, id 0, lun 0

---

### Post by taurus on 2006-03-11
Try
```

sudo mkdir /media/usb
sudo mount -t vfat /dev/sda /media/usb

```
Just so you know, the mount command by itself will tell you what are partitions being mounted on your system right now...  If you want to mount something, you need to tell it the filesystem, which device, and the mount point!  Type "man mount" at the prompt for more info.

---

### Post by Scunizi on 2006-03-21
I was having problems mounting my USB MP3 player from Creative (Rhomba). It also acts like a mass storage device.  I'm also fairly new at this operating sys so when I was playing around with your suggestions I came up with this....
sudo mount -t vfat /dev/sdc1 /media/usb and it mounted just fine.  Of course it won't automatically mount it...yet... and I had to create a directory called usb inside of media (another hurdle).  But it now works!  I tried previosly with just using sdc as one of the parameters but ended up having to put a 1 at the end.  Strangely enough, my usb memory stick mounts all by itself even with the MP3 player mounted!  Now I just have to figure out how to make it automount:-k 
Any suggestions?

---

