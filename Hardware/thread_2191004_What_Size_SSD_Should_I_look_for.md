---
title: "What Size SSD Should I look for"
date: 2013-11-30
forum: Hardware
---

### Post by chandler_bailey4 on 2013-11-30
Hi, I'm looking at SSDs for my eMachines desktop PC that dual-boots Ubuntu 13.10 (x64) and Windows 7 Home Premium (x64).

This one stood out to me [http://www.amazon.com/Kingston-Digital-2-5-Inch-SV300S37A-120G/dp/B00A1ZTZOG/ref=sr_1_1?s=electronics&ie=UTF8&qid=1385828623&sr=1-1](http://www.amazon.com/Kingston-Digital-2-5-Inch-SV300S37A-120G/dp/B00A1ZTZOG/ref=sr_1_1?s=electronics&ie=UTF8&qid=1385828623&sr=1-1)

but I was wondering if I'd be better off with the 60 gb model for $50 or the 120 for $70. Let me know what you think

---

### Post by rackit on 2013-11-30
Double the storage for $20 more sounds like a better value to me. I have experienced the need to upgrade firmware on certain Samsung (not Kingston) SSDs to get them to work with current kernels, just a heads-up.

---

### Post by chandler_bailey4 on 2013-11-30
How difficult would it be to replace a 1TB HDD with the 120gb SSD, hardware-speaking? I want to fresh install both operating systems and use Ubuntu as my primary OS (Win7 just for printing)

---

### Post by Bashing-om on 2013-11-30
chandler_bailey4; Hi !

I gotta chime in ! Why replace ? Why not add ?
SSD as the primary hard drive and the 1tb hard disk secondary/storage and what ever ??

I believe; 
no such thing as too much ram, no such thing as too much storage

---

### Post by rackit on 2013-11-30
Should be pretty straight forward. Are you going to us the TB drive for data? If you just use windows to print, have you considered a VM (VirtualBox) and just print from within that? BTW what can't you print from Linux that you need to have Windows to print? unsupported printer perhaps?

---

### Post by Bashing-om on 2013-11-30
chandler_bailey4; Yeah !

^ What he (rackit) said.

[INDENT][INDENT]why didn't I think of that
[/INDENT][/INDENT]

---

### Post by chandler_bailey4 on 2013-11-30
Yeah, it's a Canon Pixma MG3222 that isn't completely supported. Can't do color and it prints a lot slower than it does on Windows. I should try setting up a VM like that. Is it hard to set an SSD as primary and make the HDD for the data?

---

### Post by rackit on 2013-11-30
I use fstab to mount my data drive. You can put where ever you want. I usually do ~/data if I'm the only one using it, otherwise, /mnt/data, or something like that. Make sure owner and group are set to allow you wr access to it.

---

### Post by chandler_bailey4 on 2013-11-30
As quite a beginner, how difficult would all of this setup be?

---

### Post by rackit on 2013-11-30
Here are the community docs [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) if you need a hand, repost.

---

### Post by chandler_bailey4 on 2013-12-01
My last question: what are the odds that, in physically installing the SSD, that I'll screw something up with my system? I'm new to tweaking with hardware and don't know how in-depth it would be just to add the drive.

---

### Post by SuperFreak on 2013-12-01
You should not have major difficulty it is just a matter of screwing the SSD into the case and connecting the power supply and SATA connection (connect to motherboard SATA connection and SSD connection.)
The one thing you should be aware of is that static from your person discharged to the interior of case will damage the electronics. By touching the metal of the case(if it is a steel case) or other metal surface (ie radiator) just before you start working on the inside of the case you will discharge excess static on your person. Or you can buy a antistatic wrist strap from your local computer supply store


edit: Not sure if this is essential but you might want to put the SATA coonnection for the SSD  in the number 1 SATA connection on motherboard and move the TB connection to the number 2 position on motherboard so it boots in the right order

---

