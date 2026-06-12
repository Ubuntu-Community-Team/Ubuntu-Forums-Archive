---
title: "Athlon LE-1640 +  HD4870 why no work?"
date: 2013-05-27
forum: Hardware
---

### Post by FED UP on 2013-05-27
I've been using an old Emachines with an Athlon LE-1640. This is the best rig I have access to. I like to watch HD videos, and do some light gaming. Full HD videos will play locally, but keeps my CPU at 90-95% usage the entire duration. Streaming HD from online? Forget it. CPU jumps to 100% and video skips and stalls horribly. (my connection is more than enough to handle the data). I had a Powercolor HD4870 lying around, so I installed that. The card itself functions just fine. I have an ample PSU. There is no change in performance. I get ~1fps in Unigine Heaven.
I checked BIOS to make sure that PCIE was enabled, and it is. I went ahead and re-installed Lubuntu 13.04 with the card already in, so the configuration would be made via install/setup. Still no joy. 
I suspect a BIOS issue, i have Phoenix Technologies 6.00 PG. 
INIT DISPLAY FIRST is set at PCIEx.
im having trouble figuring out how to get this HD4870 to play nice.
Ive done alot of googling and other digging, and tried numerous remedies, all to no avail.
Any direction would be greatly appreciated. I'm pretty new to linux.
Tutorials?
Advice?
anything helpful would be great!

---

### Post by QIII on 2013-05-27
Hello and welcome to the Forums!

Which version of Ubuntu are you using?

Thanks.

---

### Post by FED UP on 2013-05-27
I'm running Lubuntu 13.04
Also, I'm suspecting a BIOS issue, because there are other settings besides "init display first" which I dont understand.
I have RESET CONFIG DATA [disabled]
RESOURCES CONTROLLED BY [auto(ecsp)]
PCI/VGA PALETTE SNOOP [disabled]

Or a driver problem, maybe?

---

### Post by FED UP on 2013-06-02
> **QIII said:**
> Hello and welcome to the Forums!

Which version of Ubuntu are you using?

Thanks.

Hey thanks, I went to the ATI wiki link in your sig. Followed instructions, and via terminal commands, I'm showing that a Radeon driver is active. However, im still getting zero benefit from the 4870. I don't understand what's going on here. I'm not dumb, I'm just new to Linux, and could really use a little direction here. I've been able to solve almost every issue I've had since I started Lubuntu about 6 months ago, but this one's got me snakebit. I could REALLY use a little help.

---

### Post by Yellow Pasque on 2013-06-02
> why no work?
Your CPU is weak for video decoding and you currently don't have any video decode acceleration from the GPU.

> Tutorials? Advice? anything helpful would be great! 
Your options:
1) Go back to Ubuntu 12.04.1 and use the proprietary Catalyst/fglrx Legacy driver.  That should allow you to use XBMC or VLC (with va-api) with some acceleration: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29)

2) Try to get open-source video decode acceleration working (WARNING: it probably won't be easy/fun and you should wait for Ubuntu 13.10 if you don't know what you're doing and/or a borked system would ruin your day).
[http://www.phoronix.com/scan.php?page=article&item=amd_opensource_uvd&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_opensource_uvd&num=1)

---

### Post by FED UP on 2013-06-03
Thank you, Tem. I will look into these a.s.a.p.

---

### Post by FED UP on 2013-06-12
I havent had time to roll back to 12.04.1 yet, but today I installed an update that included xorg display drivers. I've been working overtime lately, and am wondering if this new update would help. I guess I need to look up changelog/details of the update and see if it might be the answer. I just dont have time to roll back (at least this week). Would you maintain your advice to roll back, Temujin? 
Also, if I go to 12.04.1, would I need to stop installing Ubuntu base updates? How should I handle updates if I did roll back?
I appreciate your time & advice. Thanks a ton.

---

