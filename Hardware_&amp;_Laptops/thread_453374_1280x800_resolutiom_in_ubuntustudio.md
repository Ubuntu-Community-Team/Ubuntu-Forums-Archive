---
title: "1280x800 resolutiom in ubuntustudio"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by Biblio on 2007-05-24
Hi there,

I'm a Linux newbie and just installed UbuntuStudio. I'm getting so pi$$ed off as i have no clue on how to set my resolution to 1280x800. Ive got a HP 510, I've tried that sudo dpkg-reconfigure xserver-xorg command but it doesn't work. It looks like it picks up my card as a vesa card. Can someone plz tell me what a vesa card is and to set my resolution to 1280x800? thanx

---

### Post by skirkpatrick on 2007-05-24
Don't know if this will help because I don't know which video card you have but on my Dell Inspiron 6400 with Intel video, I just had to install 915resolution from the repositories.

---

### Post by Biblio on 2007-05-24
Thanx,
 i tried that already but an error message came up saying i don have a supported chipset, my card is Intel Graphics Media Accelerator 900

---

### Post by Biblio on 2007-05-24
I noticed that there are a lot of people having problems with their screen resolutions under Ubuntu, I found it a bit strange that Ubuntu would have these kind of issues, does anyone perhaps no why this is the case? Are there also any developments being made towards say an installer like windows or OS X has that would make installing drivers and applications easier? as you know I'm a newbie to Linux and would like to learn Linux and how to use it but just finding it really difficult to make the move to Linux esp. when there is no one to teach you the OS

---

### Post by TerryL on 2007-05-24
I have 3 laptops that have had problems with the last 3 versions of Ubuntu, (Fedora, Suse and PCLinuxOS all work fine). I don't know why Ubuntu has this problem, I would have accepted it in 1 version (Dapper) as a glitch, but to fail to fix the problem in Edgy and now in Feisty just makes me wonder why I keep trying.

I know I could fix the problem by tinkering with the xorg.conf file but I don't see why users should have to, especially as other distros I try don't have the problem (it's open source so surely Ubuntu could look se what the others are doing right).

My laptops are :- 

    ASUS W3H00N with ATI Radeon 9700 and a 1280x768 screen

    Acer Aspire 1502 with ATI Radeon 9600 and a 1400x1050 screen

    Acer TravelMate 3004 with ATI Radeon 9x00 abd a 1280x800 screen

The Radeon chipset is a common and I would put the blame purely there IF other distros didn't just work, but I would PREFER to use Ubuntu.

I will say that on a refurbished IBM Thinkpad X30 with some form of Intel chipset and a 1024x768 (bog-standard) display works fine - including Desktop effects.

For now I am stuck with the Suse and PCLinuxOS (for variety) distros on those 3 machines (Fedora niggled me to death for different reasons).

Please, can the Ubuntu team sort this long standing bug out! Three versions is long enough to get it fixed surely.

---

### Post by ramjet_1953 on 2007-05-25
Try loading the new Intel driver.

Copy and paste the following command into a terminal:

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

Then re-boot and see if you have a heap of extra choices in your [COLOR="Blue"]System>Preferences>Screen Resolution[/COLOR] menu.

Regards,
Roger :cool:

---

### Post by macmatt on 2007-06-15
> **TerryL said:**
> I have 3 laptops that have had problems with the last 3 versions of Ubuntu, (Fedora, Suse and PCLinuxOS all work fine). I don't know why Ubuntu has this problem, I would have accepted it in 1 version (Dapper) as a glitch, but to fail to fix the problem in Edgy and now in Feisty just makes me wonder why I keep trying.

I know I could fix the problem by tinkering with the xorg.conf file but I don't see why users should have to, especially as other distros I try don't have the problem (it's open source so surely Ubuntu could look se what the others are doing right).

My laptops are :- 

    ASUS W3H00N with ATI Radeon 9700 and a 1280x768 screen

    Acer Aspire 1502 with ATI Radeon 9600 and a 1400x1050 screen

    Acer TravelMate 3004 with ATI Radeon 9x00 abd a 1280x800 screen

The Radeon chipset is a common and I would put the blame purely there IF other distros didn't just work, but I would PREFER to use Ubuntu.

I will say that on a refurbished IBM Thinkpad X30 with some form of Intel chipset and a 1024x768 (bog-standard) display works fine - including Desktop effects.

For now I am stuck with the Suse and PCLinuxOS (for variety) distros on those 3 machines (Fedora niggled me to death for different reasons).

Please, can the Ubuntu team sort this long standing bug out! Three versions is long enough to get it fixed surely.

I agree, wholeheartedly; this is an absolutely unacceptable, that 915resolution is installed AFTER the fact??!. I mean come ON guys - intel 900 series graphics chipsets, are not exactly a rarity these days - even "Linux Mint" liveCD (Cassandra) managed to get it right, and they manage to do so RIGHT "out of the box" even in liveCD mode.

You guys can do better - this is a MUCH needed fix, so why not fix it?!. Insanely disappointing, from a high-profile distro such as Ubuntu.

---

