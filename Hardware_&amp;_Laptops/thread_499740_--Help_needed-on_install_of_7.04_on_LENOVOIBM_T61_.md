---
title: "--Help needed-on install of 7.04 on LENOVO/IBM T61 LAPTOP--"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by seantm on 2007-07-12
Hello all,

Fristly I'm a noobie --so please excuse my ignorance --but I'm determined to use ubuntu and be a member of this community --so thanks in advance! 

I just purchased a new lenovo /IBM T61 thinkpad (lastest models with core duo & Santa Rosa) and am trying to install 7.04 Fiesty on it. This is my first expereince with installing 7.04 and it's not going well. I'm disapointed --thought it would just work like in the past. 

Upon a restart from windooze the DVD boots and begins the install just fine then stops completey displaying the folllwing message:

[B][INDENT][INDENT]
BusyBox v1.1.3 (Debian 1:1.1.3ubuntu#) built-in Shell (ash)
Enter "help" fora list of built in commands"

/bin/sh: can't access tty;  job control turned off
(initrmfs) _
[/INDENT][/INDENT][/B]

Any advice about how to proceed from here would be greatly appreciated!  TIA -seantm

---

### Post by seantm on 2007-07-13
[B]FYI: AN UPDATE on Fiesty 7.04 install on Lenovo/IBM T61 
[/B]

Well after some research I've  learned that the initial install issue has to do with the DVD drive detection. To make it work one must go into the BIOS and switch from "SATA" to "COMPATIBLE" to make it work. From here the install can begin.

However, in Live CD many things are still not working out of the box i.e., sound, wifi, desktp effects, different screen resolutions (1600x800 default is all) so  it appears that Fiesty 7.04 is really not so up to standard for the latest offering from Lenovo IBM...  Inquires suggest it will take* a lot *of tweaking just to get these basic functions working. Quite disapointing when you consider that according to the posts here Fiesty 7.04  worked great out of the box with the T60 and so many other IBM/Len laptops.. So new buyers beware or be prepared for this... Perhaps the new gutsy release will address these shortcomings... hope so...

BTW here my config -very basic really nothing too fancy: 

Intel Core 2 Duo T7100 (1.8 GHz 800MHz 2MBL2)

2GB DDR2 PC2-5300 667mhz

15.4 WXGA TFT WideScreen

80 GB 5400RPMHarddisk

DVD-ROM Combo 24X Max, Ultrabay Slim

ThinkPad 11a/b/g Wi-Fi wireless LAN Mini-PCIe US/EMEA/LA/ANZ

Microsoft Win Vista Home Basic

9 cell Li-Ion Battery

1 Yr Depot Warranty

CONFIGURED SYSTEM
6465CTO CTO THINKPAD T61 WIDESCREEN-3Y

---

### Post by paulg on 2007-07-15
> **seantm said:**
> Quite disapointing when you consider that according to the posts here Fiesty 7.04  worked great out of the box with the T60 and so many other IBM/Len laptops.. So new buyers beware or be prepared for this... Perhaps the new gutsy release will address these shortcomings... hope so...


Not surprising at all as this is about as this is basically bleeding edge laptop hardware. From reports I have heard, the OS these systems are shipping with is not faring too well either....

If you haven't seen it yet, there's another [thread]("http://ubuntuforums.org/showthread.php?t=471563") of T61 owners posting tips to get various aspects working.

Also check out this [wiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61") where several posts refer back to.

Anyway, best of luck! Support *will* improve especially as more Santa Rosa systems hit the market.

---

### Post by jb1789 on 2007-07-15
I would have to agree that newer hardware does not work well with Ubuntu yet.  I have a new Dell Latitude D830 Santa Rosa system that is barely functional.  For me, the Live CD did not work (I received a similar error), but the Alternate CD did allow me to install Ubuntu and boot into a command line interface (safe mode) to edit some files to get a working GUI.  If you still haven't installed Ubuntu, I would recommend using the Alternate CD.

---

### Post by seantm on 2007-07-18
Thanks for your reply... I was kind of hoping that I wouldn't have to spend hours tweaking Ubbuntu to get it to work but it looks like that's what's neccessary....

---

### Post by seantm on 2007-07-18
Thanks for the comment... Do you think that gutsy will have gresater support?

---

### Post by ubanchaos on 2007-07-18
gusty prolly will have better support

---

### Post by seantm on 2007-07-18
hope so --be a shame to  have to ubuntu just "kinda, sorta" work on the latest advances in hardware and have to constantly patch, tweak and modify just to get it to full functionality.... After all hat's why we all dislike windows ---unfinished, poorly working OS's that need constatn maitainance --not to mentionthe costs..

 The beauty of Ubuntu is that it ussually "just works" and better thasn most OS's...

---

