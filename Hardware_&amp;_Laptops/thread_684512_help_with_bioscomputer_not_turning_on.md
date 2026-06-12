---
title: "help with bios/computer not turning on"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by miesnerd on 2008-02-01
Hey all-
I had my 64 bit ubuntu installed. I worked wonderfully. I got 4GB of ram that I ordered, so I tried to install it. I've installed ram before, so this shouldnt have been a problem.
I turned off and unhooked the computer and moved away from the carpet and set the computer down on the ground. I unbolted the case and touched several parts of the case (to get rid of static charge) and I pulled out the old ram (1 GB) and placed the new 2x2 GB OCZ ram in the first two dual channels. Put the old ram (1 GB) in the 3rd slot. Tried it. Comp turns on, fans go, no signal to the monitor. I switched it around, and same result. Third time I tried it without any ram to see if it would boot at all. Then I tried it again with just the original ram. The last two times my comp turned on, no signal to the monitor, and then the system started making a series of three beeps. What did I do? I keep reading that i may need to reset the CMOS. Is that the case or does it sound like I fried something. I just bought this computer last week so Im checking into the warranty in case that becomes relevant.
The motherboard is:
Asus M2A-VM AMD 690G Chipset DDR2/800 SATA RAID PCI-Express MBoard w/Radeon X1250 Graphic

and 400 watt power supply
if you need more details to help, let me know.
Thanks in advance.

miesnerd

---

### Post by miesnerd on 2008-02-01
i just thought of a little info that may be applicable:
-fans all work. Even the one directly on top of the CPU itself. 
- Power does not seem to be getting to the USB components.

---

### Post by Mantis86 on 2008-02-01
Bad memory is usually represented by  3 short beeps... check your mobo manual to be sure tho

---

### Post by miesnerd on 2008-02-01
> **Mantis86 said:**
> Bad memory is usually represented by  3 short beeps... check your mobo manual to be sure tho

Thanks for the help man. The mobo manual really didnt specify much. I was disappointed last night. I'll look again tonight.
A few questions:
Does that mean that all three 3 dimms are bad, or just the first one I touched (the 1 GB one.
I tried to have just the 2x2  GB ram in there without the 1 GB one. No go. So is it possible its all three 3 dimms that are bad? Seems unlikely...

---

### Post by Bartender on 2008-02-01
The motherbaord won't post with no RAM at all.  You've gotta have some functioning RAM.  BIOS beep codes are fairly standardized, just have to find the beep codes for your BIOS.  A few minutes on the internet should yield results if you can't find anything in the manual.

Figure out which memory slot is your #1 slot.  If you're testing memory sticks and put it in a secondary slot it might not work.

Also, I don't think you can run dual-channel memory, then just toss one stick of RAM in an extra slot.  There's usually a setting in BIOS to run memory as dual-channel or single.  If you're running dual-channel it's gotta be dual-channel, not some weird combination.  Set RAM back to single-channel in BIOS, then test your RAM one stick at a time in the #1 slot.

If they all seem OK, set memory back to dual in BIOS and only populate the two appropriate slots.

---

### Post by oldsoundguy on 2008-02-01
A way to test that memory .. plug in the one you KNOW is good (the old one) and boot.  Make sure it at least posts.  Shut down and plug in the next stick and boot .. if it boots do the third one.  Somewhere along the line, is something is amiss, it will not boot!

And the worry about static is blown all out of proportions .. handling the ram should NOT do damage to it.  ALL that has to be done to dissapate the static is to TOUCH the power supply box while you are unplugging the computer (touch first then unplug).  I have built several dozen computers and static electricity has not been a problem .. (unless you live in a super dry area where you get doorknob shock all the time!)

---

### Post by miesnerd on 2008-02-01
as an update, I have relatively good news.  Right now, when I start up the computer, there are no beeps and I have all three DImms installed.
However, i after it hits the motherboard screen ( i guess that's calle POST), it doesnt do anything.
One time (when I only had the one DIMM in, it clearly was okay, as it let me go into GRUB.
Now, i have the two 2 GB dimms in the 3rd and 4th slot, and it says at the bottom of the screen as it POSTS (i believe) "hit delete to setup or tab to see POST".
Neither button is responsive. What now?

---

### Post by Yellow Pasque on 2008-02-01
Put one DIMM in so that you can get into the BIOS/setup. Then you can increase the RAM voltage (try 2V to start, and don't go higher than 2.2V) and relax the memory timings to CAS5 or 5-5-5-18. After you save those settings, then turn off the computer and try installing the 2GB sticks.

Are you using 64-bit Ubuntu? That's the only way you can take advantage of 4 (or more) GB RAM.

---

### Post by miesnerd on 2008-02-01
> **Temüjin said:**
> Put one DIMM in so that you can get into the BIOS/setup. Then you can increase the RAM voltage (try 2V to start, and don't go higher than 2.2V) and relax the memory timings to CAS5 or 5-5-5-18. After you save those settings, then turn off the computer and try installing the 2GB sticks.

Are you using 64-bit Ubuntu? That's the only way you can take advantage of 4 (or more) GB RAM.

Thanks for your help man, and yes, I am running 64 bit linux.
Now where Im at is that I have 4 GB in, and detected (so that means that no dimms are damaged).
The comp boots into GRUB, and I select ubuntu. However, 1/3 of the way thru the install, (tried on two different monitors) the screen goes black and doesnt come back. What gives?

Also, i Havent done the CAS5 5-5-18 thing, because I dont know what that is. Is there another name for it? I didnt see anything that looked similar in my options to edit.

Miesnerd

---

### Post by miesnerd on 2008-02-02
bump

---

