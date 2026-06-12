---
title: "Laptop Specs - Hardware compatibility?"
date: 2014-04-05
forum: Hardware
---

### Post by nico16 on 2014-04-05
Hi, 

I'm planning to get a laptop configured and use Ubuntu 12.04 on it. 
Has anyone got some knowledge about whether the hardware I have chosen will work fine with Ubuntu (especially bluetooth / wifi / camera)?

Any advice / comments much appreciated. 

cheers

- - - -

Chassis & Display
UltraNote: 15.6" Matte HD LED Backlit Widescreen (1366x768)

Processor (CPU)
Intel® Core™i5 Dual Core Mobile Processor i5-4310M (2.70GHz) 3MB

Memory (RAM)
8GB SAMSUNG 1600MHz SODIMM DDR3 MEMORY (1 x 8GB)

Graphics Card
INTEL® HD GRAPHICS MEDIA ACCELERATOR 4600

1st Hard Disk
750GB WD SCORPIO BLACK WD7500BPKX, SATA 6 Gb/s, 16MB CACHE (7200 rpm)

1st DVD/BLU-RAY Drive
UltraNote Series: 8x SATA DVD±R/RW/Dual Layer (+ 24x CD-RW)

Memory Card Reader
Internal 9 in 1 Card Reader (MMC/RSMMC/SD: Mini, XC & HC/MS: Pro & Duo)

Thermal Paste
ARCTIC MX-4 EXTREME THERMAL CONDUCTIVITY COMPOUND

Sound Card
Intel 2 Channel High Definition Audio + MIC/Headphone Jack

Wireless/Wired Networking
GIGABIT LAN & WIRELESS INTEL® AC-7260 (867Mbps, 802.11AC) + BLUETOOTH

USB Options
2 x USB 3.0 PORTS + 2 x USB 2.0 PORTS AS STANDARD

---

### Post by sikander3786 on 2014-04-05
The best thing to do will be to boot a Live Ubuntu USB and test all your hardware. Otherwise, all of that hardware sounds familiar and should be compatible with Ubuntu.

---

### Post by ajgreeny on 2014-04-05
This must be a listing from the UK PCSpecialists, from whom I bought my last desktop machine (it is great too).  Are you aware that they have a Linux forum at their website [PCSpecialist Linuxforum]("https://www.pcspecialist.co.uk/forums/forumdisplay.php?32-Linux") and you may get some good answers there, even though the company does not officially support Linux, from other users who have already tried it out.

For my part I can not see anything that should cause you a problem.  You can even buy without an OS if you want to, which is the way I made my purchase.
There's a thread at [https://www.pcspecialist.co.uk/forums/showthread.php?32611-Ultanote2-with-Debian-Wheezy](https://www.pcspecialist.co.uk/forums/showthread.php?32611-Ultanote2-with-Debian-Wheezy) about a very similar machine that had some problems with debian but ran Ubuntu 13.10 with no problems, so I think you should be fine.

---

### Post by nico16 on 2014-04-06
Thanks for the replies! 

Yep, this is from PCspecialist, well spotted. I posted on their forums a couple of days ago but have had no reply as of yet :( so thought I would ask on an ubuntu dedicated forum.

I am still not sure whether to order with or without an OS. Ideally I wouldnt want to pay the Microsoft tax but I worry about PCspecialist support in case anything does not work 100% fine or if any part breaks down at some point (given they dont officially support linux as you rightly said). Have you had any such problems ajgreeny? What has been your experience of their support generally?

Apart from that, I now anticipate that compatibility should be fine with Ubuntu. Only thing Ive read is that Blue Ray does not always work very well with linux but im not sure how much this is a problem, plus im not sure im gonna use blue ray that much anyway.

cheers

---

### Post by ajgreeny on 2014-04-06
No problems really other than my misunderstanding of UEFI when booting the install medium; I did not realise two versions of the boot device will show, one for UEFI and the other for legacy BIOS.

I used UEFI and followed all the advice at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") which got me out of the difficulty pretty quickly.

I had great support before buying the machine, both from PCS, and via the forum.  My chosen motherboard/cpu combination was not actually shown in the configuration options as that m/b does not allow over-clocking but the cpu does, however, I wanted that cpu (Intel-i5-3570K), for the HD4000 graphic chip.  A question to PCS staff quickly came back with the answer that the m/b was in fact compatible with the 3570K version of the cpu, but space simply did not allow every possible option to be shown.  I was told to order the machine with the i5-3570 cpu then send a message asking that it be upgraded to the i5-3570K, and all was changed very quickly over email and at a minor cost.  Superb service in my opinion.

I did have a hardware problem with the memory card reader which worked with some types of cards, but refused to see any SDHC or normal SD cards.  I emailed PCS and a replacement reader was arranged, along with permission for me to open the case and replace the faulty hardware with no loss of warranty cover; try doing that with most high street retailers.

If it is of any consequence to you, I must say that when making that change to the card reader, I could see how carefully all cables and general interior layout of hardware had been carried out; no stray wires or bits and pieces as there were in my previous box.  This gives me great confidence in the company and its machines, which has been confirmed by the way this machine runs.

The PCS linux forum is not the quickest around, and certainly nothing like this one, which in my experience is the best I have ever used, but it does have some very experienced users who post very useful answers.

---

### Post by nico16 on 2014-04-06
Thanks for your reply. Sounds all good to me.
Cheers for the tip about uefi too. Will make sure i do things properly when installing ubuntu.

So, just to make sure, when you had your memory card reader problem, were you using ubuntu only (as opposed to dual boot)? And where PCS happy to go with your diagnosis that it was faulty, even though they could not check themselves on a windows OS? Great if if thats the case.

I will stick around on their forums for a bit longer but yes, so far experience on this forum has proven better!

---

### Post by ajgreeny on 2014-04-06
> **nico16 said:**
> Thanks for your reply. Sounds all good to me.
Cheers for the tip about uefi too. Will make sure i do things properly when installing ubuntu.

So, just to make sure, when you had your memory card reader problem, were you using ubuntu only (as opposed to dual boot)? And where PCS happy to go with your diagnosis that it was faulty, even though they could not check themselves on a windows OS? Great if if thats the case.

I will stick around on their forums for a bit longer but yes, so far experience on this forum has proven better!
Yes, after a few questions to make sure I was not putting the SDHC card in the wrong slot, or upside down, and that the card I was using was a good one (it was as it is still in use in my camera), they accepted that it was faulty hardware.

They originally said they wanted the old card-reader back, but when they sent the new one they said not to bother, so I binned it.  It was a few minutes job to replace the old for new in the desktop machine, but that might have been more difficult in a laptop, though they do allow opening up laptops as well as desktops if necessary, without loss of warranty cover.

I was and remain very impressed with the company, the machine I purchased, and their helpful trading methods, so I would not hesitate to use them again for any new computer needed in this household.

---

### Post by nico16 on 2014-04-07
Ok, thanks a lot for your replies, very helpful.

---

