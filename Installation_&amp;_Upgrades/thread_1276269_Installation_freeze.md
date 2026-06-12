---
title: "Installation freeze"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by mokfarg on 2009-09-26
I have decided to try Linux after using Windows for years. I am frustrated at the experience so far. I can't get Linux to install and I am clueless on how to fix whatever the issue is. After trying Ubuntu and receiving an error I tried Fedora as well with no success. 

I tried two versions of Ubuntu the official version and a daily build both with the same error. One of the versions was Ubuntu 9.10 AMD64 Alternate CD. Put in the disk, clicked on install. Went through the menus. Manually partitioned. I have Windows 7 as the first partition so I created a 40gb / partition using the ext4 filesystem and created a 4gb swap. I then am able to go through installing all the software without any visible errors. Grub installed without errors to the MBR. Then the Window pops up "finish the installation" the PC reboots. Grub boot loader comes up and I choose Ubuntu. Next I see a few errors right afterwards:

Firmware bug powernow k-8 
ata1 softreset failed device not ready
ata2 softreset failed device not ready
ata3 softreset failed device not ready
skipped: aptuser """ '"""' " firefox (can't remember the whole path)


After this error messages, it continues to a blue ubuntu graphical loading screen with a bar going across. Next it gets to a brown screen for logging in and this is where things stop. I can move the mouse curser but that is it. I see my login name but can't interact with it. Also the box has a but of a graphic issue around the edges of it. So this is as far as I can go. Appears to be a video card issue considering it starts at the desktop. This is just a guess but my video card is about 5 years old. To test further I enabled my integrated video card on the motherboard and recieved the same error.

I did the disk check and the disk integrity was fine. I have had windows xp pro 64bit, windows ent 7 64bit installed to the same PC without any issues. The hardware I believe is fine. I was unable to find any information on my specific hardware having issues with ubuntu or linux in general on the web. My video card is far from new, I imagine it would be okay with ubuntu.

I have updated the BIOS to the latest version for my motherboard. And tried again with no success. I really want to learn linux but this is a harsh start. I was hoping to learn it slowly and wean off of windows. Any ideas? If you give any suggestions, please remember i know nothing about linux. Please be very detailed so I can follow your directions. Thanks for the help, I hope to be using linux soon.

[AMD Phenom 9850 2.5GHz Socket AM2+ 125W Quad-Core Black Edition Processor ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103286")

[ASUS M3A78-EM AM2+/AM2 AMD 780G HDMI Micro ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131324")

[OCZ Reaper HPC 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory Model]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227289")

Nvidia 7800 GT video card PCIe

2 SATA harddrives (set to AHCI in bios) Not raided

---

### Post by mokfarg on 2009-09-26
I am able to boot command line only w/ networking

---

### Post by mokfarg on 2009-09-26
I need a guru's kindness, I really want to make my start into Linux. : D

---

### Post by oboedad55 on 2009-09-26
> **mokfarg said:**
> I need a guru's kindness, I really want to make my start into Linux. : D

Did you perhaps try a 32-bit version of Linux, say 9.04? 9.10, of course, is still in alpha testing and for some of us that means nasty bugs...

---

### Post by mokfarg on 2009-09-26
I would dislike to use a 32bit because I have 4gb of ram. I will download the supported current version of ubuntu 64bit and give that a go.

---

### Post by mokfarg on 2009-09-29
I took your advice and tried the live ubuntu 9.04 cd 64bit and had the same results. Ubuntu loads the desktop up to the point I hear the sign on sound theme and the little round cursor just stops spinning around. I can see the desktop with a bit of distortion around some boxes and can not interact with anything. I am able to move the cursor.

Any ideas on how to fix this or even narrow it down? Is there not some text log file that shows where the system freezes? Any help will be greatly appreciated for this Linux newbie. Surely this isn't some rare problem, others must have experienced this. Sounds like a video card issue but from what I have read my older 7800gt has been supported now for sometime. 

I have tried other distros to investigate and all do the same thing, freeze while desktop is loading. In OpenSUSE's failsafe mode everything actually loaded up and I was able to use the system but couldn't figure out why regular mode wouldn't work. I would prefer to use Ubuntu or get both distros working to have a rpm and a apt-get system running. Thank you ahead of time. I really hope someone can lay out a path of troubleshooting for me I can follow.

I haven't a clue, please help. Thank you.

---

### Post by mokfarg on 2009-09-30
Please help? Is there no one that knows how I should proceed on solving this issue?

---

### Post by oboedad55 on 2009-09-30
> **mokfarg said:**
> Please help? Is there no one that knows how I should proceed on solving this issue?

Dude, I'm just responding because you sound so lonely. Your problem is indeed strange. My experience with getting answers here is that if it's something people don't know how to fix you won't get a lot of feedback. It's very possible that there really is no one here who knows the solution. Folks aren't staying away just to cause you more difficulty. I've had the same experience as you with this one. I've even posted questions and had no response at all. I hope somebody has a solution for you. It may well be an impossible hardware conflict.

---

### Post by mokfarg on 2009-09-30
> **oboedad55 said:**
> Dude, I'm just responding because you sound so lonely. Your problem is indeed strange. My experience with getting answers here is that if it's something people don't know how to fix you won't get a lot of feedback. It's very possible that there really is no one here who knows the solution. Folks aren't staying away just to cause you more difficulty. I've had the same experience as you with this one. I've even posted questions and had no response at all. I hope somebody has a solution for you. It may well be an impossible hardware conflict.

Well I'm not lonely just wanting to find a solution to this issue.:confused: I have always heard how friendly the communities are in linux and how they are happy to help. I tried a suggestion then posted back as I think one should. I also asked again to move the post up where maybe someone with this knowledge may see it and be able to give me some suggestions. I am not knowledgeable at all when it comes to linux. I do know though that with Windows I can pin point issues with certain troubleshooting methods, I was hoping to be able to do the same in linux. Anyhow my last post, if no one can solve this issue or at least direct me to how to troubleshoot and pinpoint what the issue is, I am just out of luck.

---

### Post by l3th0x on 2009-10-14
Hi,


Could you post all the error message?

I use to have a "similar"  thing (I do not remember all the message) and I resolved by adding "all_generic_ide"  in grub.

I do not know if it is the same thing that happened to me, but, if you want,  you could give this a try..

Press esc when grub loading message appear, then "e". Select kernel line, press again "e" and add "all_generic_ide".

I remembered that it use to happen in two pcs, when I upgraded to 9.04 (but I do not remember  all the error message, seems something similar to this...that is why I am telling that I am not sure if this is going to be the solution) . At the very end, I downgrade one to 8.10 due to this solution did nothing :confused:, the other (have different hardware) was solved with this.:P

Hope that helps...

Regards!

---

