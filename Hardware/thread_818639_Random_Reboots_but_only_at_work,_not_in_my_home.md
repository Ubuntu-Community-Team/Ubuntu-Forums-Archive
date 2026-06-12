---
title: "Random Reboots but only at work, not in my home???"
date: 2008-06-04
forum: Hardware
---

### Post by pettsium on 2008-06-04
Hi.

I'm new to the forum and in no way an expert, so apologies for my lack of knowledge.

I'm running a Philips X58 freevents laptop, Intel core 2 duo, 2Gb RAM. I have Windows Vista and Ubuntu 7.10 as a dual boot system.

My problem is this. My laptop refuses to work for more than an hour when I am in the office. It will randomly reboot throughout the day, and after reboots will hang on the Intel screen before it reaches the Grub Loader. Specifically after it says mouse initialized. This is about three quarters of the way to loading before the grub screen appears.

When at home it works fine. I will run it all day at the weekend (18hrs+) with no reboots at all. and the tasks I perform are exactly the same. The difference at home is that I use a wireless network and at work an Ethernet connection. But even with the Ethernet cable out the same behavior occurs. There is no discernible difference in temp between the two environments. I have tried unplugging it and running off battery at work and still get the reboots.

I am baffled. Please shed light on this weird behavior.

Thanks in advance, Andrew

---

### Post by bapoumba on 2008-06-04
Any particular electrical or magnetic equipment around at work ?

---

### Post by pettsium on 2008-06-04
Thank you for your swift reply. This problem is really bugging me!

There are other desktop pc's around and laptops but no equipment that would give off a stong magnetic field. Other peoples laptops seem to work just fine in the shared area.

Could it be an electical/magetic issue?

---

### Post by bapoumba on 2008-06-04
Well, I'm not sure, but if your laptop behaves that way on battery and without the ethernet cable plugged in, and works fine at home, must be some form of a field (magnetic or other, I'm not to knowledgeable in this area). Any neon lamp, other sort of light bulb, big electrical outlet behind the wall ?

---

### Post by pettsium on 2008-06-05
Don't think thee is any equipment that could be causing it. I have just managed an hours work and it has rebooted. Last night it ran at home for 8 hours.

What else could it be? Need help people!!

---

### Post by BUSHYBOB on 2008-06-05
Try running it at home with the wireless router switched off. It may be something looking for the wireless router.

---

### Post by pettsium on 2008-06-06
Switched off router last night and laptop worked fine.

Really not sure what could be causing this. SMNP was mention by one of our tech guys, can this cause reboots across a network?

---

### Post by acron1 on 2008-06-06
Is this only happening with Ubuntu or does it also happen when you are using Windows at work?

I must say that if it happens in Windows as well electrical/magnetic interference, as the other poster suggested, seems to be the logical explanation.

---

### Post by NewbieNeedsHelp on 2008-06-06
Couldn't figure out why my desktop was doing that at my brother's house. One time I noticed the lights dim. Turns out that when my sister-inlaw turned on the clothes dryer downstairs, the power draw in this older house was a problem. Went to Micro House and bought a $ 100 UPS, (APC brand, don't buy Belkin, they're junk), ... problem solved. Maybe the AC or some other electrical device is kicking on at work.

---

### Post by wpshooter on 2008-06-06
Are you **SURE** that you are using **ALL** of the **exact same **hardware equipment/perpherials, mouse, external keyboards, printers, etc., etc. that you are using when you are at home ?

---

### Post by pettsium on 2008-06-06
Don't really use windows at work. Will try it though, as that would eliminate  Ubuntu being the issue.

As to whether it is the exact setup at both locations, the only peripheral I use is a usb mouse, and I use that at woek and at home. No external keyboard etc is use in either location.

---

### Post by ridshack on 2008-06-07
Hmmm, I would assume you are doing something a bit different between sites. 

For trouble shooting purposes I would recommend booting to a different OS as you suggested.

I would be curious to see the results of running a bootable system stress test at home for several hours and at the office for several hours. 

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

My hunch is its not your environment. 

With a laptop on battery I dont think unclean power will affect your system the same as a desktop.

Someone would need to authenticate to SNMP to attemp executing any commands. you can ```
telnet localhost 161
``` to test if snmp is listening. 

Keep us updated.

Ridshack

---

### Post by pettsium on 2008-06-09
Hi all. Thanks for your replies.

Will download the stress test cd and give it a go.
What exactly does this do and what will it tell me about my system or my problem? 

Am working from a different desk now, to test whether it is a dodgy socket/ghost at my desk.

Fingers crossed the prob will be solved this week

---

### Post by bapoumba on 2008-06-09
> **pettsium said:**
> Hi all. Thanks for your replies.

Will download the stress test cd and give it a go.
What exactly does this do and what will it tell me about my system or my problem? 

Am working from a different desk now, to test whether it is a dodgy socket/ghost at my desk.

Fingers crossed the prob will be solved this week

Just out of curiosity, would you please post here if you find a solution to this situation?

---

