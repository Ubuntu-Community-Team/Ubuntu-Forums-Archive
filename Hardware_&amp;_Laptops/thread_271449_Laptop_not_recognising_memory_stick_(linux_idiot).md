---
title: "Laptop not recognising memory stick (linux idiot)"
date: 2006-10-04
forum: Hardware &amp; Laptops
---

### Post by peabee on 2006-10-04
I've just put Ubuntu 6.06 on my Tiny laptop. 
I've got the printer working and Skype, along with other easy bits. 
I need to be able to use my memory stick to download pictures from my camera for eBay :)
So....I insert thememory card....
...no what?

I know this makes me sound like an idiot but I'm used to the 'reassuring' beeps and messages of Windows...and now I hear nothing. 

Thanks for your patience and any ideas. 

If I can get this working I *may* tackle the issue of installing my webcam :o)

Thanks
PB

---

### Post by mark_g on 2006-10-04
So there's no icon on your desktop showing you the memory stick, right?
If you could tell me more about the type of memory stick, I might be able to help you out.

---

### Post by peabee on 2006-10-04
Thanks Mark, 

It's an 8MB Sony Memory Stick (not Pro or the other one)
The card reader on the laptop can read most card (not sure how many though).
It did work in Windows well. 
If I go to Places -> Computer there are only 2 items in there...The DVDRW drive and File System (Which I assume is the HDD :) )
Thank you
Patrick

---

### Post by mark_g on 2006-10-05
Firstly, check that the appropriate checkboxes are checked in System > Preferences > Removable Drives and Media and then the tab 'Storage', so that your media is automounted. It probably is, but just to make sure.

You can try to mount it manually:
> 
sudo mkdir /mnt/myusb
sudo mount -t vfat /dev/sda1 /mnt/myusb

You may need to change /dev/sda1 to /dev/sda2 or so.

Before you can remove it, execute

> umount /mnt/myusb

Let me know if this works

---

### Post by Josh1 on 2006-10-05
Hi,
You may also want to try and just plug in your camera straight into ubuntu by USB (I'm guessing it has USB).
All the cameras i've tried with this it worked perfectly without any tweaks/modifications :D.
Cheers,
- Josh

---

### Post by peabee on 2006-10-05
OK here we go :)
Checked System -> Preferences -> Removeable Drives and Media. In 'Storage' the top three (Mount, Mount and Browse) options are ticked.
Plugged the Memory Stick in again....
Places -> Computer - there is nothing in there to do with the memory stick. 

Tried the following (with the memory stick plugged in):

> peabee@peabee-laptop:~$ sudo mkdir /mnt/memorystick
Password:
peabee@peabee-laptop:~$ sudo mount -t vfat /dav/sda1 /mnt/memorystick
mount: special device /dav/sda1 does not exist
peabee@peabee-laptop:~$ sudo mount -t vfat /dev/sda1 /mnt/memorystick
mount: special device /dev/sda1 does not exist
peabee@peabee-laptop:~$ sudo mount -t vfat /dev/sda2 /mnt/memorystick
mount: special device /dev/sda2 does not exist
peabee@peabee-laptop:~$ sudo mount -t vfat /dev/sda3 /mnt/memorystick
mount: special device /dev/sda3 does not exist
peabee@peabee-laptop:~$


Hmmm :)

I'also plugged the camera in but can't find a program to test it - it's the Logitech QuickCam Pro 5000 which, by searching the forums, requires some reasonable knowledge of Linux = sadly lacking in my case.  I shall research some more. 

Thanks for your help......any more??? :o)
PB

---

### Post by peabee on 2006-10-08
Still nothing.
I don't want to have to resort back to XP but I fear I may have no choice. 
Any help would be appreciated as business has had to stop because of this. 
Thanks
P

---

### Post by fedupwithwin on 2006-10-10
I have basically the same problem and no one seems to have an definitive answer.  I'm using a 128 Meg - USB V1.1 stick using FAT file system.  The stick itself has no brand name - it was a freebee I got from an Adept Robotics training class (their controllers run a version of unix).  I'm running Ubuntu Dapper Drake (6.06?) and have downloaded all the updates.  Whenever I plug in the memory stick, the volume name appears momentarily in the file browser and then dissapears entirely.  Apparently, lots of people have been having similar problems but you don't see too many answers.  I think this one needs to be kicked up to the developer level.  Also, Right now, I'm sitting at work on my office windows machine with this memory stick plugged in and I have no problems.  H'mmmm, maybe if I search the forums using a different keywork like "flash disk"?  I'll give this a wirl and come back...

---

### Post by fedupwithwin on 2006-10-10
Nothing Yet.....  Seems as if the Kernal is having some trouble recogizing some types of USB controllers installed on various motherboards.  Last night I checked the system log file after plugging in the same stick ( and getting the same result ) and it said something to the effect that it did not get a proper response from the motherboard USB controller chip.  Unfortunatly, I can't post this right now since I'm at work (and really should be working).  I don't think the motherboard controller chip is a dud cause' it worked fine with XP (installed previously).  I wonder if this is a response time issue whereas XP - running a bit slower on this machine - might by it's nature wait a little longer for the proper responses from the USB controller chip.

ANY TAKERS???

---

### Post by krisbowen on 2006-10-10
I have had the same problem, my work around is to power off the machine..plug the usb memory stick in the power on..it loads itself no problems and is able to be accessed..short term fix for me until I learn more about Ubuntu!!

---

### Post by fedupwithwin on 2006-10-10
I'm Baaaaaaack!  This time plugged in the memory stick, an instance of the nautilus file manager opened up and all my files on the memory stick were shown.  When I tried to open a file on the memory stick however, the device listing promptly disappeared from the file manager.  One interesting note though: before I plugged in the stick I tried the command "lsusb" to list my available usb busses and it showed two active busses.

??????@??????-desktop:/$ lsusb
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

But after plugging in the memory stick and having it fail, I get only one active usb bus.

??????@??????-desktop:/$ lsusb
Bus 001 Device 001: ID 0000:0000

What I probably should have done is to run that command while it seemed to have mounted everything properly and before it actually failed.  Maybe next time...

Also. listed above in this thread someone mentioned trying to mount /dev/sda1  I looked in that directory - "sda1" is not listed as a possible device - there is no mention of it in the /dev directory.  Am I understanding this correctly?

Please somebody help - I'm really trying to make this work.

---

### Post by fedupwithwin on 2006-10-10
OK, I'm still looking for a reason why Dapper won't read my memory stick.  I opened up my /var/log/syslog file and posted what I thought was the parts that show the systems actions when it tryed to recognise/mount the memory stick.


Oct 10 20:10:09 localhost kernel: [17186242.520000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Oct 10 20:10:09 localhost kernel: [17186243.260000] SCSI subsystem initialized
Oct 10 20:10:09 localhost kernel: [17186243.348000] Initializing USB Mass Storage driver...
Oct 10 20:10:09 localhost kernel: [17186243.348000] scsi0 : SCSI emulation for USB Mass Storage devices
Oct 10 20:10:09 localhost kernel: [17186243.348000] usb-storage: device found at 2
Oct 10 20:10:10 localhost kernel: [17186243.348000] usb-storage: waiting for device to settle before scanning
Oct 10 20:10:10 localhost kernel: [17186243.348000] usbcore: registered new driver usb-storage
Oct 10 20:10:10 localhost kernel: [17186243.352000] USB Mass Storage support registered.
Oct 10 20:10:15 localhost kernel: [17186248.356000]   Vendor: usb1.1    Model: Flash Disk        Rev: 2.00
Oct 10 20:10:15 localhost kernel: [17186248.356000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Oct 10 20:10:15 localhost kernel: [17186248.392000] usb-storage: device scan complete
Oct 10 20:10:15 localhost kernel: [17186248.488000] Driver 'sd' needs updating - please use bus_type methods
Oct 10 20:10:15 localhost kernel: [17186248.500000] SCSI device sda: 257312 512-byte hdwr sectors (132 MB)
Oct 10 20:10:15 localhost kernel: [17186248.508000] sda: Write Protect is off
Oct 10 20:10:15 localhost kernel: [17186248.508000] sda: Mode Sense: 0b 00 00 08
Oct 10 20:10:15 localhost kernel: [17186248.508000] sda: assuming drive cache: write through
Oct 10 20:10:15 localhost kernel: [17186248.532000] SCSI device sda: 257312 512-byte hdwr sectors (132 MB)
Oct 10 20:10:15 localhost kernel: [17186248.540000] sda: Write Protect is off
Oct 10 20:10:15 localhost kernel: [17186248.540000] sda: Mode Sense: 0b 00 00 08
Oct 10 20:10:15 localhost kernel: [17186248.540000] sda: assuming drive cache: write through
Oct 10 20:10:15 localhost kernel: [17186248.540000]  sda: sda1
Oct 10 20:10:15 localhost kernel: [17186248.552000] sd 0:0:0:0: Attached scsi removable disk sda
Oct 10 20:10:15 localhost kernel: [17186248.580000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 10 20:10:16 localhost kernel: [17186249.864000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Oct 10 20:11:08 localhost kernel: [17186301.360000] uhci_hcd 0000:00:07.3: host system error, PCI problems?
Oct 10 20:11:08 localhost kernel: [17186301.360000] uhci_hcd 0000:00:07.3: host controller halted, very bad!
Oct 10 20:11:08 localhost kernel: [17186301.360000] uhci_hcd 0000:00:07.3: HC died; cleaning up
Oct 10 20:11:08 localhost kernel: [17186301.360000] usb 2-1: USB disconnect, address 2
Oct 10 20:11:08 localhost kernel: [17186301.360000] sd 0:0:0:0: rejecting I/O to device being removed
Oct 10 20:11:08 localhost kernel: [17186301.360000] Buffer I/O error on device sda1, logical block 50892
Oct 10 20:11:08 localhost kernel: [17186301.360000] lost page write due to I/O error on sda1
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 503) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 504) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 505) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 506) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 507) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 508) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 509) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 510) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 511) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 512) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 513) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 514) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 515) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 516) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 517) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 518) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 519) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 520) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 521) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 522) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 523) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 524) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 525) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 526) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 527) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 528) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 529) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 530) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 531) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 532) failed
Oct 10 20:11:08 localhost kernel: [17186301.468000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.468000] FAT: Directory bread(block 533) failed
Oct 10 20:11:08 localhost kernel: [17186301.468000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.468000] FAT: Directory bread(block 534) failed
Oct 10 20:11:08 localhost kernel: [17186301.600000]  0:0:0:0: rejecting I/O to dead device
Oct 10 20:17:01 localhost /USR/SBIN/CRON[8040]: (root) CMD (   run-parts --report /etc/cron.hourly)


DOES ANYBODY HAVE A CLUE?  ](*,)

---

