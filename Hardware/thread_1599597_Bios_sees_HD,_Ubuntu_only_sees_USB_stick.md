---
title: "Bios sees HD, Ubuntu only sees USB stick"
date: 2010-10-18
forum: Hardware
---

### Post by ericbrooking on 2010-10-18
I've build a new computer for Ubuntu only.
Luanched it off the USB stick so that I could format HD and install Ubuntu on it.
Bios sees the Crucial 256G SSD but Ubuntu does not.
In Terminal code : cd /dev
                           ls hd*
finds nothing??????
 
A little help would be great. Ubuntu has worked well for me on a machine that had windows already but I should be able to fire up a system with only Ubuntu, yes?  I would hate to think that I would have to buy windows just to get Ubuntu to work.
 
Thanks.
  Eric

---

### Post by mastablasta on 2010-10-18
SSD ? Could it be Ubuntu doesn't support this particular drive?
 
Anyway instead of buying windows ( i am assuming you plan to buy them in order to format the drive?!) you could maybe try with FREEDos?!

---

### Post by Fafler on 2010-10-18
It's /dev/sd*, not /dev/hd*.

Edit: Why not let the installer handle it?

---

### Post by ericbrooking on 2010-10-18
> **mastablasta said:**
> SSD ? Could it be Ubuntu doesn't support this particular drive?
 
Yeah, I don't see why it shouldn't work, it's a standard replacement in laptops.
 
Anyway instead of buying windows ( i am assuming you plan to buy them in order to format the drive?!) you could maybe try with FREEDos?!
 
If I can just get the drive formated it may work fine??  Hopefully someone smarter than me can help.  It just seems like there are very few people doing new ground up Ubuntu machines out there? Everyone is loading it onto a Windows or Mac, and heck why pay for that?
 
Thanks
  Eric

---

### Post by ericbrooking on 2010-10-18
> **Fafler said:**
> It's /dev/sd*, not /dev/hd*.
 
Edit: Why not let the installer handle it?
Edit: The installer doesn't see the drive, I assumed it was because the drive isn't formatted?
 
I'm probably wrong but it seemed that /dev/sd* reported back just the memory stick that I'm running Ubuntu off of? I'd sure like to get it on the SSD HD.
 
Any help would be greatfully appriciated. The manual is great for setting up dual boot or converting a windows system but it lack in the clean ground up Ubuntu system.
 
Eric

---

### Post by Fafler on 2010-10-18
Post the results of
```
dmesg | grep sd
```

---

### Post by ericbrooking on 2010-10-18
> **Fafler said:**
> Post the results of
```
dmesg | grep sd
```
 
I'm not able to copy and paste because right now but it came back with
sd 6:0:0:0: Attached SCSI generic sg0 type 0
...some more stuff about this drive along with 4GB... this is my usb stick that i'm running Ubuntu off of.  There is no other drives mentioned.
 
???

---

### Post by ericbrooking on 2010-10-18
> **mastablasta said:**
> SSD ? Could it be Ubuntu doesn't support this particular drive?
 
Anyway instead of buying windows ( i am assuming you plan to buy them in order to format the drive?!) you could maybe try with FREEDos?!
 
FREEDos will give me a FAT32 file system instead of a EXT3 or EXT4.  I'm trying to make a fast read/write machine.  Is there much difference between the three?

---

