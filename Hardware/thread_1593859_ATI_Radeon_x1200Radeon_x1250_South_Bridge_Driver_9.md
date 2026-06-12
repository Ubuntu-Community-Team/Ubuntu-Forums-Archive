---
title: "ATI Radeon x1200/Radeon x1250 South Bridge Driver 9.1"
date: 2010-10-11
forum: Hardware
---

### Post by xovertheyearsx on 2010-10-11
Straight forward question!

****************
*What Happened?*
****************
I've been enjoying linux and wanted to run a full fresh install
of the OS, but I keep running in to Graphics Compatability Issues. I've been researching my issue for the past month or so and what I found out was the 22 Radeon Graphics Chipsets have been dropped as of mid 2009. Their idea is to "focus on future products". It sounds like utter crap to me, but here I am now with a legacy chipset. The Drop affected Windows XP, Windows Vista, Windows 7, and Linux Distributions. I noticed there are no Proprietary Drivers Supported beyond Karmic Kola 9.10 and Lucid Linx 10.04.1 dropped complete support, so even the fglrx supported drivers only support Catalyst Control Center 9.3 and Higher, I need Catalyst Control Center 9.1 since its the last version that supports my chipset.

*************
*My Question*
*************
Is there a **non** *fglrx Proprietary Driver* which i can install on Ubuntu 10.04.1 Lucid Lynx? Or at least an alternative set of drivers I can install, even if they are Linux Distributed, for my chipset? If there is, how I could I do it and where can I find the software I need?

*************
*My Hardware*
*************
***Below are my hardware settings for both laptops I use, They use almost identical chipsets.***

Laptop 1: 
RS690M Chipset
Toshiba Satellite A215-S7414
ATI Radeon Integrated Graphics Card
x1250 Series

Laptop 2:
RS690M Chipset
Toshiba Satellite L305D-S5895
ATI Radeon Integrated Graphics Card
x1250 Series

---

### Post by Yellow Pasque on 2010-10-11
Straightforward answer: (!)
> **xovertheyearsx said:**
> Is there a **non** *fglrx Proprietary Driver* which i can install on Ubuntu 10.04.1 Lucid Lynx?
No.

> Or at least an alternative set of drivers I can install, even if they are Linux Distributed, for my chipset? If there is, how I could I do it and where can I find the software I need?
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
Good luck.

---

### Post by stlouisubntu on 2010-12-05
> **xovertheyearsx said:**
> Straight forward question!

****************
*What Happened?*
****************
I've been enjoying linux and wanted to run a full fresh install
of the OS, but I keep running in to Graphics Compatability Issues. I've been researching my issue for the past month or so and what I found out was the 22 Radeon Graphics Chipsets have been dropped as of mid 2009. Their idea is to "focus on future products". It sounds like utter crap to me, but here I am now with a legacy chipset. The Drop affected Windows XP, Windows Vista, Windows 7, and Linux Distributions. I noticed there are no Proprietary Drivers Supported beyond Karmic Kola 9.10 and Lucid Linx 10.04.1 dropped complete support, so even the fglrx supported drivers only support Catalyst Control Center 9.3 and Higher, I need Catalyst Control Center 9.1 since its the last version that supports my chipset.

*************
*My Question*
*************
Is there a **non** *fglrx Proprietary Driver* which i can install on Ubuntu 10.04.1 Lucid Lynx? Or at least an alternative set of drivers I can install, even if they are Linux Distributed, for my chipset? If there is, how I could I do it and where can I find the software I need?

*************
*My Hardware*
*************
***Below are my hardware settings for both laptops I use, They use almost identical chipsets.***

Laptop 1: 
RS690M Chipset
Toshiba Satellite A215-S7414
ATI Radeon Integrated Graphics Card
x1250 Series

Laptop 2:
RS690M Chipset
Toshiba Satellite L305D-S5895
ATI Radeon Integrated Graphics Card
x1250 Series


Friend, you are absolutely right in that to lose full functionality when upgrading you OS is a REGRESSION and should be unacceptable. 

[https://bugs.launchpad.net/jockey/+bug/576206](https://bugs.launchpad.net/jockey/+bug/576206)

My solution was to roll my own Debian Lenny and a half which ended up being a 2.6.29 kernel (64-bit) ext4, grub2, fglrx 8.593, xorg 7.3, which gave me back full functionality of my integrated laptop ATI graphics card after losing it by installing Ubuntu lucid.

The following two links were instrumental although it took time and was a bear from start to finish (I now know what they mean when they say "Ubuntu" is Zulu for can't install Debian.

[http://kmuto.jp/debian/d-i/](http://kmuto.jp/debian/d-i/)
(install the 2.6.30 version and later downgrade to 2.6.29)

[http://smxi.org/site/faqs-sgfxi.htm](http://smxi.org/site/faqs-sgfxi.htm)

Once the 2.6.29 kernel, kernel headers, and kbuild are installed, the do an Alt-F2, log-in, switch to root, kill gdm, x, and then do an sgxfi -o 9-3 (after installing sgfxi.)

If you need assistance tracking down some of the resources, let me know and I will try to help.  We may no longer be able to get the .debs for the 2.6.29 kernel as of this date anymore.

ATI and Ubuntu should not drop support for this cards many of which are not more then two years old.

---

### Post by Yellow Pasque on 2010-12-05
> The following two links were instrumental although it took time and was a bear from start to finish
You could have just installed Ubuntu Hardy/8.04

---

### Post by mastablasta on 2010-12-06
> **Temüjin said:**
> You could have just installed Ubuntu Hardy/8.04
 
Hardy will stop being supported in April while Lenny will probably be supported for some time to come.

---

### Post by stlouisubntu on 2010-12-06
> **Temüjin said:**
> You could have just installed Ubuntu Hardy/8.04

Thanks for the comment, friend.  However, Hardy/8.04 is what I had before I installed Lucid/10.04 as a reinstall / upgrade.  In preparation, using gparted I shrunk my old ext3 /home partition and created a new ext4 one and rsync'd the old to the new.  Then I deleted my old ext3 / partition and then created a new ext4 one.  After that I then proceeded with my 64-but Ubuntu Lucid install and much to my dismay the current version of fglrx would no longer run on my ATI Xpress 200M integrated laptop graphics card.

You are correct in that I could have gone back to hardy/8.04, but I would have had to go back to ext3 / grub legacy as well and was not yet willing to do that.

That is why I call my current install Debian Lenny and a half as it is running linux-2.6.29 / ext4 / grub2 while standard Lenny runs linux-2.6.26 / ext3 / grub legacy.  I know my kernel is not supported with security updates but I had to make a tradeoff.  I will likely keep this until about a year after Squeeze is released, perhaps longer.

---

