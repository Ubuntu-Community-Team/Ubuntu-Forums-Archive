---
title: "[SOLVED] Resolution Problem"
date: 2008-09-08
forum: Hardware
---

### Post by flamingswrd on 2008-09-08
I have just recently installed Ubuntu on an old box and now my screen resolution is stuck between 800x600 and a lower setting. I figure the problem is  driver but I do not know what hardware the computer is running with (video anyway...). I believe it is using onboard graphics...
Anyway, long story short:
1) Is there a way to find out what graphics card/motherboard graphics I am using? If so, how?
2) I'm wiling to bet it is embedded, so does embedded video need a driver?
3) Does Ubuntu have an easy fix for this sort of problem? 

*Note: I know the monitor is capable of higher resolutions since it used to run XP. I have tried installing the windows restricted drivers, but they didn't help.

Help is appreciated!

---

### Post by phidia on 2008-09-08
Open a terminal and enter > lspci | grep VGA That will provide the card you have. Check the [wiki]("https://help.ubuntu.com/community/Video") for further info.

---

### Post by flamingswrd on 2008-09-08
I tried doing what the wiki said but no results. Here is what the command you gave me resulted in if it helps for reference. 

lspci | grep VGA 
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

---

### Post by flamingswrd on 2008-09-09
Is this type of integrated graphics incompatible with Linux?

---

### Post by phidia on 2008-09-09
What happened when you entered this in a terminal: > sudo apt-get install xserver-xorg-video-openchrome From [Wiki guide]("https://help.ubuntu.com/community/OpenChrome") for unichrome cards. Your card is supported-how well is the question. Can you provide the rest of your system specs-memory particularly?

---

### Post by flamingswrd on 2008-09-13
I apologize, my internet was down for a while. Anyway, I found another graphics card that fits my system, but it will not show anything when plugged in. I figure it is a driver problem, but I do not know where/how to get one for it. Here is what I got in the terminal

lspci | grep VGA
00:08.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

*The first is the card I added, the second is the on-board graphics of the motherboard. 

If you need more system information, I would be glad to supply it, but I am still learning terminal commands and do not know which one to use.

---

### Post by flamingswrd on 2008-09-17
Instead of endlessly searching for a driver for onboard or a card, I just opted to find a cheap, linux supported card. Thanks for your assistance anyway.

---

