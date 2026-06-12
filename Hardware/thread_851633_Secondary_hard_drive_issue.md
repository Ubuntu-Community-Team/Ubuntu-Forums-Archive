---
title: "Secondary hard drive issue"
date: 2008-07-06
forum: Hardware
---

### Post by Drenhead on 2008-07-06
I am trying to install a secondary 500 GB hard drive on an older Dell system that apparently won't recognize a drive larger than 200 GB.  The BIOS sees a hard drive, but doesn't see how large it is or the brand or anything.

When booting, I get an error saying "error autosensing hard drive on Primary Drive 1"

I am trying to have a dual boot Win XP and Ubuntu system.  If I was to install a IDE controller card, would my bios boot correctly and see the drive?  I was going to load XP on the 200 GB drive, and ubuntu on the 500 GB drive.  Do I have to load Windows before I can use the controller card?  Not sure how those work.

Thanks in advance.

---

### Post by red_team316 on 2008-07-06
IF you were to install an IDE controller card, it should see your other drives. I did this on an old P3 box and it worked great. 

I've never heard of that kind of BIOS problem, although you might look on DELL's site for a newer BIOS for that motherboard. If you go this route, I would contact tech support first to find out for sure, as flashing the BIOS is inherently risky.

I know some BIOS'es allow you to input info on the drive as far as size/sectors/etc... you might try that to get it to recognise it.

---

### Post by Drenhead on 2008-07-06
Thanks for the reply.

I have the latest BIOS from the Dell website.  With the IDE controller card, will it recognize the new drive at boot time, or only after the OS loads?  Meaning, can I install Ubuntu on the drive that is connected to the controller card?

---

### Post by red_team316 on 2008-07-06
> **Drenhead said:**
> With the IDE controller card, will it recognize the new drive at boot time, or only after the OS loads?  Meaning, can I install Ubuntu on the drive that is connected to the controller card?
Yes, you should be able to. It should recognise the card as well as any hard drives hooked up to it before any bootloader is encountered. If not, I would find a different controller card.

---

