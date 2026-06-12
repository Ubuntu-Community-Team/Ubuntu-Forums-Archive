---
title: "USB memory stick woes"
date: 2006-10-11
forum: Hardware &amp; Laptops
---

### Post by fedupwithwin on 2006-10-11
I tried to post this problem in another thread as requested by the moderators of this site but, have not been able to get anywhere.  So, I created a new thread and posted some of the previously posted items.  Hopefully someone will have some ideas...


- This time plugged in the memory stick, an instance of the nautilus file manager opened up and all my files on the memory stick were shown. When I tried to open a file on the memory stick however, the device listing promptly disappeared from the file manager. One interesting note though: before I plugged in the stick I tried the command "lsusb" to list my available usb busses and it showed two active busses.

??????@??????-desktop:/$ lsusb
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

But after plugging in the memory stick and having it fail, I get only one active usb bus.

??????@??????-desktop:/$ lsusb
Bus 001 Device 001: ID 0000:0000

What I probably should have done is to run that command while it seemed to have mounted everything properly and before it actually failed. Maybe next time...

Also. listed above in this thread someone mentioned trying to mount /dev/sda1 I looked in that directory - "sda1" is not listed as a possible device - there is no mention of it in the /dev directory. Am I understanding this correctly?

Please somebody help - I'm really trying to make this work.

OK, I'm still looking for a reason why Dapper won't read my memory stick. I opened up my /var/log/syslog file and posted what I thought was the parts that show the systems actions when it tryed to recognise/mount the memory stick.


```
Oct 10 20:10:09 localhost kernel: [17186242.520000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Oct 10 20:10:09 localhost kernel: [17186243.260000] SCSI subsystem initialized
Oct 10 20:10:09 localhost kernel: [17186243.348000] Initializing USB Mass Storage driver...
Oct 10 20:10:09 localhost kernel: [17186243.348000] scsi0 : SCSI emulation for USB Mass Storage devices
Oct 10 20:10:09 localhost kernel: [17186243.348000] usb-storage: device found at 2
Oct 10 20:10:10 localhost kernel: [17186243.348000] usb-storage: waiting for device to settle before scanning
Oct 10 20:10:10 localhost kernel: [17186243.348000] usbcore: registered new driver usb-storage
Oct 10 20:10:10 localhost kernel: [17186243.352000] USB Mass Storage support registered.
Oct 10 20:10:15 localhost kernel: [17186248.356000] Vendor: usb1.1 Model: Flash Disk Rev: 2.00
Oct 10 20:10:15 localhost kernel: [17186248.356000] Type: Direct-Access ANSI SCSI revision: 02
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
Oct 10 20:10:15 localhost kernel: [17186248.540000] sda: sda1
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
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 503) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 504) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 505) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 506) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 507) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 50 failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 509) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 510) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 511) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 512) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 513) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 514) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 515) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 516) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 517) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 51 failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 519) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 520) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 521) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 522) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 523) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 524) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 525) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 526) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 527) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 52 failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 529) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 530) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 531) failed
Oct 10 20:11:08 localhost kernel: [17186301.464000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.464000] FAT: Directory bread(block 532) failed
Oct 10 20:11:08 localhost kernel: [17186301.468000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.468000] FAT: Directory bread(block 533) failed
Oct 10 20:11:08 localhost kernel: [17186301.468000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:11:08 localhost kernel: [17186301.468000] FAT: Directory bread(block 534) failed
Oct 10 20:11:08 localhost kernel: [17186301.600000] 0:0:0:0: rejecting I/O to dead device
Oct 10 20:17:01 localhost /USR/SBIN/CRON[8040]: (root) CMD ( run-parts --report /etc/cron.hourly)
```

- Any ideas???

This memory stick works fine in XP but everytime I plug it into my Ubuntu machine, it shuts down the USB port.  I believe there is hardware/software compatibility issue with this particular type of USB host controller.  I do not know which type of controller it is, nor do I know how to access that information.

My Ubuntu machine is a gateway desktop with an AMD Athlon 1100.

---

### Post by dannyboy79 on 2006-10-11
Oct 10 20:11:08 localhost kernel: [17186301.468000] FAT: Directory bread(block 533) failed
Oct 10 20:11:08 localhost kernel: [17186301.468000] 0:0:0:0: rejecting I/O to dead device
By this it appears that Ubuntu is having trouble reading the filesystem! Also, if you want to find out what usb controller you are using just type in lspci -v. It should be in there. That's about all the help I can provide.

---

### Post by fedupwithwin on 2006-10-11
Huh! I didn't realise the USB host controller sat on the PCI bus.  I guess it would have to though...  I'm not real familiar with PC achitecture (obviously).  I'll give that command a try when I get home tonight.  In the meantime, since I'm not getting too many helpful responses here.  How should I proceed?  I am a relatively compentant Control Systems Engineer with about twenty years experience in design/build/programming of custom-high speed assembly automation.  If someone might give me a basic foothold to get started, maybe I could tear this thing apart and find a solution.

  The initial questions I have along these lines are:

- What programming language do I need to learn.  I've taught myself many programming languages, any new one shouldn't be a huge challenge.

- What programming developemt tools/environments are available.

- Judging from the log file listing above, where would be a good place to start fiddling?

---

### Post by christhemonkey on 2006-10-11
> Oct 10 20:11:08 localhost kernel: [17186301.360000] uhci_hcd 0000:00:07.3: host system error, PCI problems?
Oct 10 20:11:08 localhost kernel: [17186301.360000] uhci_hcd 0000:00:07.3: host controller halted, very bad!
Oct 10 20:11:08 localhost kernel: [17186301.360000] uhci_hcd 0000:00:07.3: HC died; cleaning up

That sounds the worst bit?

maybe some hardware IRQs interrupting each other?

But i suppose that would affect windows as well...

---

### Post by dannyboy79 on 2006-10-11
> **fedupwithwin said:**
> 
  The initial questions I have along these lines are:

- What programming language do I need to learn.  I've taught myself many programming languages, any new one shouldn't be a huge challenge.
What you want to accomplish using linux would determine what langauges you need to learn?

> **fedupwithwin said:**
> 
- What programming developemt tools/environments are available.

I have no idea, i am not a programmer and in fact I am just a linux newbie trying to help fellow Ubuntu users. I am bored at work. You don't by chance work at Rockwell Automation. You did mention the Automation industry?

> **fedupwithwin said:**
> 
- Judging from the log file listing above, where would be a good place to start fiddling?

I would say, copy all your info off the drive first, then reformat using ubuntu, format it again as fat32, then check it in xp first if it reads it, then put all your stuff back on it. That would be about all i can suggest being a newbie.

---

### Post by fedupwithwin on 2006-10-11
Dannyboy79 - Yes I'm in the automation industry but, I don't work for Rockwell.  I do however use a quite a few of their products from time to time.  If you are an applications engineer for Rockwell or if you are a Philadelphia-area vendor of their products, you probably already know me...

I'll try your suggestion of re-formatting my memory stick under Ubuntu.  That sounds like a logical suggestion.  I've been a little hesitant to try plugging another USB device into this system.  I just bought a 1G stick and I don't want to screw it up due to a hardware handling issue.

As far as what type of programming I would like to do.  I figure that I could at the very least, analyse the existing USB driver source and run a few tests to see if I can improve things.  I imagine it would take me a little while but, with winter coming, I won't be getting out much anyway.

---

### Post by fedupwithwin on 2006-10-12
Oops!  Is it possible to reformat a memory stick in Ubuntu if I can't get the thing to mount in the first place? Ah well, back to the docs...

---

