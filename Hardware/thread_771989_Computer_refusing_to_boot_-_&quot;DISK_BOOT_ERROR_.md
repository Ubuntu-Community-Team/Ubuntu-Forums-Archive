---
title: "Computer refusing to boot - &quot;DISK BOOT ERROR - DISK NOT FOUND&quot;"
date: 2008-04-28
forum: Hardware
---

### Post by Eax.exe on 2008-04-28
Hello everyone

I've had this home-build computer for around 2 years.

Just recently it started to refuse to boot.
It loadede the BIOS and just before it's supposed to load GRUB it
said: "DISK BOOT ERROR - DISK NOT FOUND". It doesn't say that anymore though.

Now it just shows "ACPI CONTROLLER   9" (it's a part of the PCI Device Listing)

I've tried googling it and I've switched the PCI cabels between the CD and the Harddrive.

Does anyone have any idea what to do?

Some specs:

Athlon ati a8n-sli
nVidia G-Force 7800gt
2gb ram
200gb
Linux Ubuntu Feisty Fawn

It's also unable to boot from CD and Floppy

I tried changing the harddrive, didn't work.

---

### Post by bigken on 2008-04-28
try setting your bios to default also try shorting the cmos battery

---

### Post by encompass on 2008-04-28
Those are very much, hardware issues...
When you go into your bios do you see your cdrom?  If not there there is some hardware issues that need to be addressed.
It could be something had just come loose.
Make sure all parts of your computer are plugged in.  Like you pci slots and other what not.

---

### Post by Eax.exe on 2008-04-28
> **bigken said:**
> try setting your bios to default also try shorting the cmos battery

Already done that :) But thanks :)
How do I short the cmos battery?

> **encompass said:**
> Those are very much, hardware issues...
When you go into your bios do you see your cdrom?  If not there there is some hardware issues that need to be addressed.
It could be something had just come loose.
Make sure all parts of your computer are plugged in.  Like you pci slots and other what not.

Yes it's there :)
Will do (again) :) But it didn't work last time :/

---

### Post by bigken on 2008-04-28
ok pull everything from the mobo ie modems ect and try the hdd on each ide channel 
if this dont work your mobo is damaged

---

### Post by encompass on 2008-04-28
I agree with the above... 
If you can't get any ide devices your motherboard is kaput.  Bummer man...

---

### Post by Eax.exe on 2008-04-28
> **bigken said:**
> ok pull everything from the mobo ie modems ect and try the hdd on each ide channel 
if this dont work your mobo is damaged


Will do later on :)

But I already switched the IDE between my CD drive and my HDD.

---

### Post by bigken on 2008-04-28
have you had any power surges lately also I would try another psu you never know

---

### Post by Eax.exe on 2008-04-28
> **bigken said:**
> have you had any power surges lately also I would try another psu you never know

No :(

PSU?
Power Supply Unit?

---

### Post by bigken on 2008-04-28
> **Eax.exe said:**
> No :(

PSU?
Power Supply Unit?


yep

---

### Post by Eax.exe on 2008-04-28
> **bigken said:**
> yep

Unfortunately I don't have one available :(

---

### Post by Eax.exe on 2008-04-28
WUHUU :D I made it Boot on Gutsty Live CD ^^
Will see if I can make it boot from Harddrive now :)

---

### Post by Dynamo_Joe on 2008-04-28
I'm Fiesty and (tried) using the onboard (VIA) SATA controller ... everything seems to be working fine until I tried to use the DVD burner connected on the secondary IDE channel as "Master" ... DVD drive was not found ... to cut a long story short, the new SATA hard drive that I had installed was conflicting ... my temporary solution was to removed the SATA hard drive (the DVD burner became good) ... just brought myself a new Silicon Image SATA PCI controller card ... haven't had time to install and test it yet ... if it ain't broke ... it'll wait until I get round to installing "Hardy". 

Apologies for the long post (and assumptions) ... hope this info helps.

---

### Post by bigken on 2008-04-29
> **Eax.exe said:**
> WUHUU :D I made it Boot on Gutsty Live CD ^^
Will see if I can make it boot from Harddrive now :)



well did you get it to boot from the hdd ?

---

### Post by Eax.exe on 2008-05-04
> **bigken said:**
> well did you get it to boot from the hdd ?

Yes, after re-installing Feisty.

What I did:

When it booted i kept pressing F8 until a Boot order window showed up, then I started the Feisty Live-CD and installed it again :)

Thanks a lot for everyones help :)

---

