---
title: "Need installation help!!"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by Chiron090 on 2008-12-15
Hi, thanks in advance for the help. To begin with, let me say that I am very new to Ubuntu and Linux, and my knowledge of computers in general is quite lacking, so I may need a good deal of help.

First off, I have an Hp Pav. ZE4400, with an AMD Athlon 4 2400+ processor, currently running Windows XP.  In short, this comp is OLD and will not run windows well so I am trying to completely switch to Ubuntu Desktop 8.10.

Let me also say that I have (after much much trying) finally gotten Wubi, in Windows, to run Ubuntu. (I'm on it now) Everything seems functional, all of my hardware, so I don't think that is an issue. 

Now, as far as actually installing it as my OS, I've gotten all important files off my comp in preparation. I have downloaded the live cd and burned it to an ISO image using InfraRecorder.  When I pop it in, restart, enter BIOS, and select boot from CD-ROM I get the correct screen. I have checked the CD for defects, fine as far as I can tell.  If I select "try without changes to comp" it will begin loading and one of several things will happen every time. A long list of errors, a blinking cursor that does nothing, or the comp will spontaneously restart or turn off.  This is the same when I try to just install it. Also, I had similar problems trying to get Wubi to work, it will run perfectly about 1/16 of time though.

Reading other posts I have tried pressing f3/f6 (I can't remember w/o being there) and typing 'acpi=off'  and that did not work. Although, I don't know if I did thet correctly.  I have tried writing the cd at slower speeds, and I have tried installing version 7.10, all with no success. 

I am wondering if XP is interfering with my install and if restoring my comp to factory settings and then installing Ubuntu would fix the problem, but, 1) If it still doesn't work I don't have the Windows install CD's, and, 2) I don't really know how to do that (I turned off system restore a while ago because it was eating too much memory, also there's no option for factory settings)

I apologize for the length of this post, I just wanted to be as comprehensive as possible. Any help is very appreciated.

---

### Post by taurus on 2008-12-15
Try the alternate CD and don't forget to burn it at a slow speed.

---

### Post by Chiron090 on 2008-12-15
Thanks, downloading it right now.  Will update if it works, or I run into a snag.

---

### Post by Chiron090 on 2008-12-16
[update]

So, it seemed like it was going to work, however, there are corrupt files and it cannot proceed with installing the base.  I have downloaded about 6 different ISOs, and burned even more CDs, using different speeds.  None of them are uncorrupted, they all fail the integrity check.  Today I plan on using a different comp, a different burn program, and a different brand of CD. I must say though, I am having my doubts about success.  If anyone has experienced this and has advice, much appreciated.  Or if there is a way to quickly and cheaply get a working CD sent to me, that would be awesome.  I feel like technology hates me right now.

---

### Post by taurus on 2008-12-16
Before you start the burning process, do a checksum to make sure the integrity of the ISO is good.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso](https://help.ubuntu.com/community/BurningIsoHowto?highlight=(burn)|(iso))

---

### Post by doobiest on 2008-12-16
I doubt the issue is with the ISO it self. 

I'd first look at the blank media and the burner as the culprit.

Ideally downloading the ISO onto a different PC, different disc, different burner, you get the idea.  

Next I would move onto hardware issue with the computer.  When you get to the ubuntu boot screen on the CD it might be worth running a memtest from that menu, also there is an option to check the cd for defects, i'd run that.

Also I would try swapping the IDE cables, I sound unlikely and it is, but I used to do enough comp repair where I've seen a fair share of data corruption due to faulty cables.

After that I would move onto scanning your harddrive, checking the mobo, etc.

---

### Post by Chiron090 on 2008-12-16
Thanks, I plan on trying different burning methods.  As far as the hardware, etc, stuff.  It's a laptop I'm working with (currently with no OS).  I'm using the alt. CD to curb any mem. problems. But could my issue really be hardware? I got Ubuntu to work with Wubi when it had Windows XP installed after some time, but when I did everything worked fine.  I'm just hoping I don't have to give up on Ubuntu and reinstall windows.

Ps. I'm currently using TDK CDs cause they're cheap.  Would a better quality CD perhaps fix this?

---

### Post by doobiest on 2008-12-16
I'd really want to verify the ram and cd for errors.

---

