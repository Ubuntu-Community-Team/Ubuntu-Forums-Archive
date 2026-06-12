---
title: "Tons of errors in dmesg after trying to copy files from int hdd to ext seagate hdd"
date: 2017-07-24
forum: Hardware
---

### Post by RaZoR1394 on 2017-07-24
Hi.

I bought an external Seagate backup plus 8TB hdd and I tried to copy files from one of my internal hdds. It was about 2,2TB of files. I got a warning that some files couldn't be copied so I checked dmesg and there are a lot of errors. I connected the Seagate hdd to my Mac mini to see if it was a problem with my ubuntu computer but I get error -8084. I am running Ubuntu 16.04 on my PC. The Mac Mini is running MAC OSX Sierra. I would like to know if the hdd is bad so I can return it or if the problem is something else. Thank you.

My dmesg is pasted here: [http://paste.ubuntu.com/25161455/](http://paste.ubuntu.com/25161455/) .

---

### Post by efflandt on 2017-07-24
Seagate has their SeaTools available as a DOS 8.5 MB iso file (probably FreeDOS) which I imagine could boot from CD to check and non-destructively test the drive. Info from that might be required to get warranty replacement.
[http://www.seagate.com/support/by-topic/downloads/](http://www.seagate.com/support/by-topic/downloads/)

---

### Post by TheFu on 2017-07-24
What does SMART say?  [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) and [https://help.ubuntu.com/stable/ubuntu-help/disk-check.html](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html)

---

### Post by RaZoR1394 on 2017-07-24
Sorry. I forgot to say that I checked the smart values with the disk application in Ubuntu. Everything looked good except the temperature. It said it was 55C and that the drive would soon fail. I checked the Seagate knowledge base and it said newer disks have operating temperature up to 60C. The disk is currently connected to my Mac Mini and Smart is not supported according to disk utility. I think I am going to try Seatools with one of my Windows computers.

---

### Post by TheFu on 2017-07-24
> **efflandt said:**
> Seagate has their SeaTools available as a DOS 8.5 MB iso file (probably FreeDOS) which I imagine could boot from CD to check and non-destructively test the drive. Info from that might be required to get warranty replacement.
[http://www.seagate.com/support/by-topic/downloads/](http://www.seagate.com/support/by-topic/downloads/)

Those sorts of errors probably are related to USB controllers, drivers, not a failing disk.  
I would
* Try using a different USB controller 
* There are some known issues with the kernel drivers. Some tweaks for those might be useful.  

Sadly, kernel tweaks and blacklisting the UAS driver didn't help my USB3 woes. Google finds the bug reports and suggested solutions easily. Which were more with resets and lockups that I've traced back to USB3 addon card incompatibilities.  Out of 3 USB3 devices, only 1 had that issue with that machine. The other 2 devices were completely fine on the same machine.
Moved the problem device to a newer motherboard with on-board USB3, I haven't seen any issues related to the controller.  Same kernel. Same OS release.  As far as I can see, only the motherboard and USB chips are different.  The older motherboard PCI slot is on a slow internal bus by standards today.

Many credit cards have free replacement if anything is wrong (even accident) within 90 days of purchase and/or doubles the manufacturers warranty. Dropped a HDD once while it was running - fell about 2 feet. Never worked again.  Amex gave the credit in a few days.

Of course, it is always easiest to take it back where you got it and get a replacement immediately.  Best not to mention "linux", at least that has been my experience.

---

### Post by efflandt on 2017-07-25
You do not need Windows to use the SeaTools DOS iso, if your computer can boot CD (or possibly if properly written to USB flash). Although, also testing the drive on another computer could rule out a hardware issue on that particular computer.

---

### Post by RaZoR1394 on 2017-07-26
I am well aware of that. I just connected it to another computer so that I can try another usb controller and the computer also has Windows 10 on it so I thought why not test Seatools from it to avoid fiddling with usb sticks or cd/dvds. According to Seatools SMART and the short test turned out fine. I am running the long generic test. When this is ok I am going to test copying files to it in Ubuntu 17.04 which is installed on another SSD on this computer.

---

