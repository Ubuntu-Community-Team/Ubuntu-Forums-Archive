---
title: "[SOLVED] New hard drive detected by Ubuntu... but NOT in BIOS"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by lubke2005 on 2008-01-08
Dear all,

some time ago I decided to reactivate my 3 year old ACER Aspire 1500 Laptop, which has been inactive due to a hard disk failure. I removed the faulty hardware and replaced it with new HD with identical specs (60 GB U-ATA).
As I always wanted to have a dedicated Linux-PC I downloaded the latest Ubuntu Desktop 7.10 and installed it right away from the Live CD. The installation WENT ABSOLUTELY FINE & WITHOUT ANY ERRORS!!!
After removing the CD during the first reboot the system did not boot into Ubuntu but instead told me "NO OPERATING SYSTEM FOUND".

I checked BIOS and had to find out that the HD is NOT DETECTED!!

So I launched Ubuntu again from the LiveCD and was very surprised to find out that Ubuntu had absolutely no problem in detecting/accessing the HD! I even could confirm that the first installation WENT FINE as all the Ubuntu files have been copied to the HD.

I understand that this is not really a purely 100% Ubuntu related post as there might be as well something wrong with my computer... but I would appreciate any input from people that might have a clue how to solve this issue...

Some remarks/information that might help:
- I installed Ubuntu 7.10
- I used the Ubuntu Partition Editor to access and edit the partitions... 
  everything worked just fine!
- I have the latest BIOS installed
- The exact laptop model is: Aspire 1501LMi
- my old (broken) HD is a TOSHIBA MK6021GAS / HDD2183 - 60GB
- my new HD is a SEAGATE Momentus 4500.2 / ST960822A - 60GB

Thank you very much in advance for your help!

Best regards,
Lubke2005

---

### Post by logos34 on 2008-01-08
have you tried to boot on battery power as well as AC?  Isn't there an option in the Bios to (re)detect the hard disks?  That's a strange situation...usually if the bios can't see the drive then  neither will the ubuntu installer or gnome partiition editor

---

### Post by lubke2005 on 2008-01-10
thx Logos34 for your reply,

no I did not try yet to boot in bat-mode as my batt is only working for a couple of minutes before dying. But I will try it anyway...
As for the bios-option, I was not able to find a re-detection option for HDs...
The situation is strange in deed... once in ubuntu (via liveCD), the drive is perfectly accessible!!

I will give another try tonight and report my findings...

cheers,
lubke2005

---

### Post by lubke2005 on 2008-01-10
I CAN NOT BELIEVE HOW STUPID I AM!!!

I just found the cause of the problem... The HDD's jumper-settings were still on CABLE-SELECT... after removing the jumper (master) the HDD has been detected by BIOS and FINALLY Ubuntu started without any problem!!!

Thank you both for trying to help me... 

regards,
lubke2005

---

### Post by logos34 on 2008-01-10
ah, so it was the jumper.  Funny how I never think of that possiblity in regards to notebooks, only desktops.  I'll have to remember that.

---

