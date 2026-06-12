---
title: "Can't load Ubuntu64 on my HP laptop"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by drev on 2006-11-03
I just recently got an HP Pavilion dv9000 laptop.  It's got an AMD Turion 64-bit dual core processor, 1GB Ram, etc.  When I try to load off the live boot CD I made with the 64-bit version of Ubuntu, it gets stuck loading.

I had another CD I made with the regular 32-bit flavor and used it on my Dell desktop (Pentium 4) with no problems at all.  When I throw that same disk into my laptop, it freezes during load, just like with the 64 disk.

Does anyone know what's going on?

Thanks in advance

---

### Post by john_spiral on 2006-11-03
is the live CD a 64 or 32 bit version?

---

### Post by drev on 2006-11-03
I have a 32-bit live CD and a 64-bit live CD.  Neither of them work in the laptop.

---

### Post by fatneck on 2006-11-03
Does it start to install and then hang, or nothing at all?

And do you have an ATI card in yours?

---

### Post by drev on 2006-11-03
It starts to load.  It gives me the black screen with Ubuntu logo, and begins describing what it's doing.  (Sorry for the vague descriptions; it's been ~1 week since I tried this)  Then instead of loading the GUI, it goes into a DOS/Commandline thing where it says it's loading hardware, checking if this or that works, etc.  That's where it gets stuck.

---

### Post by fatneck on 2006-11-03
Try pressing f6 (I think from memory) at the start of the install for more options and add 

noapic

that might work. Or, are there any graphics options at the install -I can't remember. I've had so many problems on my laptop I'm about to blast it and give Suse 10.1 a try :-(

good luck

---

### Post by john_spiral on 2006-11-06
go back to basics do a md5 checksum on both CDs

---

### Post by teaker1s on 2006-11-08
> **john_spiral said:**
> go back to basics do a md5 checksum on both CDs

or you may need to use alternative .iso download and use text install-this works 99% when live won't install

---

### Post by drev on 2007-02-02
How do I do a text install?

((I'm a newb =D

---

### Post by ucsdrake on 2007-02-02
it should give you the steps as you go and its the same as the GUI install (for the most part ... gets the job done in basicly the same way) but without the actual GUI istself

---

