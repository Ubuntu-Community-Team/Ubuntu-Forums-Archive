---
title: "Ubuntu freezing at startup"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by jeb800e on 2009-08-03
Is someone able to help me out here? Thanks!
[http://ubuntuforums.org/showthread.php?t=1228412](http://ubuntuforums.org/showthread.php?t=1228412)

---

### Post by lotster on 2009-08-03
All right, I've never seen your specific problem before.  But let's try... My first guess is that it's a screen card incompatibility (I know with Ubuntu's own display drivers errors hardly ever occur, but I did see a few problems on the net somewhere related to older ATI screen cards like yours).  Apparently 9.04 doesn't support the older ATI's anymore.

I can think of 2 things to try.

1, try to do an install without installing inside Windows (in other words, boot to the CD / DVD and try to install it on a separate partition, dual-booting with Windows).

2.  Try Ubuntu 8.04.  I know it's older, but it's a long-term support release, so it's supported well into 2011.  And it will probably still support your screen card...

Try the 8.04 Live CD option first to see what it's doing.

Let me know...

---

### Post by jeb800e on 2009-08-03
I have a Ubuntu *7.10* LiveCD. It seems to work fine. All I need is support for my Belkin Wireless-G Desktop Card. Can you help me out on that?

Each time I try to install 9.04 inside Windows, when I try to boot up, it always freezes once the desktop picture is shown. No buttons, no nothing!


Also, each time I have ever tried the LiveCD, the loading screen would come up, then, once it was all loaded, it would seem to glitch up or something, as the top (I would say) 25-30%portion of the screen would be black, and the rest would be similar to what you see as static on the TV, but it isn't moving. Inside the "static", I can see the Windows logo up, yet it is all screwed up and cluttered around in a certain area, like it needs to be re-aligned to fit, almost like a puzzle.

Maybe Windows has been trying to "take over" while using the LiveCD?

Thank you so much for helping me!

---

### Post by lotster on 2009-08-03
Have you tried the proprietary (non-free) drivers for the Belkin?

I have to emphasize that I still recommend rather going for 8.04 LTS, since 7.10 is only supported until this year (I'm not sure which month exactly, it may already be too late).

---

### Post by jeb800e on 2009-08-05
Where do I get those? I have tried using an open source project called MadWiFi, yet it will not work unless I have Ubuntu installed on my system. How can I install Ubuntu 7.10 without removing the rest of my partitions and Windows XP?
I tried using Wubi, again by downloading it online and waiting for Ubuntu 9.04 to download from there. When I tried to boot up Ubuntu, I got nothing but a blank, black screen.

---

### Post by jeb800e on 2009-08-06
bump...

---

### Post by Buuntu on 2009-08-06
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
See if that helps.

---

### Post by jeb800e on 2009-08-07
How do I install from my Ubuntu 7.10 disk without removing the rest of my files and Windows?

---

### Post by Buuntu on 2009-08-07
In the Live CD, go to System>Administration>Partition Editor.  From there you can shrink your windows partition.  Then on the desktop there should be an install icon.  That will then guide you through installing Ubuntu on your hard drive.  
 
Actually, you might not even need to go into partition editor, I think it lets you change that in the install program.
 
Was that what you meant?

---

### Post by jeb800e on 2009-08-07
What if I already have 3 partitions on my HDD already, and I don't want to remove my Windows copy and files?

Sorry, I'm a little new to Linux. : P Can you guide me through it, please? Thanks!

---

### Post by Buuntu on 2009-08-07
Simply start installing Ubuntu and in step 6 (I believe), it lets you play with your partitions.  If you don't want to even resize your partition (you must have SOME free space), then your only other choice is to go buy a new HDD.

---

### Post by jeb800e on 2009-08-07
Yes, I do have some free space on my partitions, but I don't know that if I install Ubuntu, will it remove everything else inside that partition? How do I install Ubuntu without removing anything? Can you guide me through, this if you can?

---

### Post by Buuntu on 2009-08-07
Ok, follow these instructions:

1. Boot from the Live CD.  You will have to change boot priority so that CD is number one, not hard drive.  You can do this by going into your BIOS settings usually by pressing a key right when your computer boots (it will usually tell you, but some common ones are Del, F1, F2, F10, and ESC)
2. In the menu that appears, select "Install Ubuntu".
3. A setup wizard should appear, follow the steps (pretty self explanatory).
4. On step 6, you can resize partitions and such.  This will NOT delete any of your files unless you specifically tell it to delete a partition.  Select the size of your Ubuntu partition based on the free space.  I would recommend at least 10 GBs to start out with, but I think you only need 2 to install it.
5.  Click next and verify all the information you entered is right.
6.  After installing Ubuntu, it well send you to a login screen where you enter the name/password you set up in the install.

If you do not know what to do in a certain spot, please be specific.  Telling me, I still need more help doesn't help me much.

---

