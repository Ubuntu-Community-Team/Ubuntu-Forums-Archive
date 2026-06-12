---
title: "cr-48 random crash and boot issues"
date: 2011-08-14
forum: Hardware
---

### Post by williamshome1 on 2011-08-14
Hello. I have a Google CR-48 test machine installed with Ubuntu 11.04. It has the Insyde H20 bios.

I'm having two issues and I'm not sure if they are related:
1. The machine will not boot after a graceful shutdown without a battery pull. Sometimes the error is "Read Error" and sometimes it says "No bootable device". If I pull the battery it will reset and boot into Ubuntu.

2. Once in Ubuntu, the operation of the machine will periodically crash. Sometimes the GUI crashes to a terminal and shows I/O errors. Sometimes, the GUI just stops responding and icons start to disappear.  I have to do a hard shutdown and battery pull to get going again.

I have reloaded the OS twice and each time wiped the drive for a fresh installation. I've also run fsck to look for drive errors and it didn't find any.

Any help and ideas are appreciated.

---

### Post by nmaster on 2011-08-14
what happens in you put back the original BIOS and reinstall ChromeOS? it should be easy to reflash the bios.  then you should see that frowny-face that asks for a recovery usb.  the steps are here: [http://www.google.com/support/chromeos/bin/answer.py?answer=1046510](http://www.google.com/support/chromeos/bin/answer.py?answer=1046510)

if it also fails when using the original BIOS and OS, then we can probably conclude that the issue is a hardware failure.

---

### Post by williamshome1 on 2011-08-14
I have not reinstalled chrome OS with factory settings yet.I'm not sure how to do that either but I believe others have already documented the steps.

Actually, I'm hoping to avoid that because I'd prefer to leave Ubuntu on the machine.

---

### Post by nmaster on 2011-08-14
> **williamshome1 said:**
> I'm not sure how to do that either but I believe others have already documented the steps.

i have a cr-48.  i already "documented the steps".  you just have to flash on the original bios.  then just plug-in the recovery usb and let google do its magic.

this should be fairly easy to do.  how did you initially flash on the Insyde bios? i know that you have to open the cr-48 case to un-ground the EEPROM, but the smart thing to do is to leave a piece of electrical tape there so that you don't have to open up the case again...

> 
Actually, I'm hoping to avoid that because I'd prefer to leave Ubuntu on the machine.
i understand this, but since you're dealing with unsupported hardware, it might be easiest to first check if the hardware is to blame.  it would be a waste to try and track down a software issue, just to find that the problem is lower level.

---

### Post by nmaster on 2011-08-14
> **williamshome1 said:**
> ...Sometimes the error is "Read Error" and sometimes it says "No bootable device"...shows I/O errors...

based on this, it could also be that you need to reseat the ssd.  you can follow these instructions: [http://cr-48.wikispaces.com/Reseat+SSD+Cable](http://cr-48.wikispaces.com/Reseat+SSD+Cable)

---

### Post by williamshome1 on 2011-08-15
OK. Thanks for the link. I did a reset on the SSD. Will see now if the problem persists.

---

### Post by nmaster on 2011-08-15
> **williamshome1 said:**
> OK. Thanks for the link. I did a reset on the SSD. Will see now if the problem persists.

while you have the case open, put a piece of electrical tape over the firmware EEPROM.  this will make your life easier if you need to flash the BIOS back.

[http://cr-48.wikispaces.com/Open+the+Cr-48](http://cr-48.wikispaces.com/Open+the+Cr-48)

---

### Post by williamshome1 on 2011-08-16
Looks like reseating the SSD did the trick. I operated a full day without either of the issues recurring. Thanks for your help!

---

