---
title: "Need to reInstall GRUB, Please help"
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by pranav on 2006-02-06
Hello

I have windows xp sp2 installed on the primary partition.
I installed Ubuntu 5.10 in one of the logical partitions. The GRUB was installed by default and everything was fine. Then I installed RedHat and there was a major problem starting Ubuntu. Trying to modify the Grub settings(through google searches) eventually screwed up everything . Now I could start win xp only.

So i have formated red hat n done away with it.

now i am left wid ubuntu n xp.

also i had given a command (after reading somewhr) fdisk /mbr

So i believe now there is no GRUB in my hard disk n win xp starts as default. Can somebody tell me how shud i reinstall GRUB n make ubuntu n Win work as before ?

I have Ubuntu install n live cds, dont have Winxp cd.

Please help me. I want to use Ubuntu again.

---

### Post by towsonu2003 on 2006-02-06
take a look at this one: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Sutekh on 2006-02-06
If you have the install CD/Live CD it should be very easy to get GRUB back.

If you want to use the Install CD try this link

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")

If you want to use the Live CD and want to preserve the WinXP bootloader in the MBR, after using **fixmbr**, follow this post

[Ubuntu Forums - HOWTO: Restore GRUB - Post #5]("http://ubuntuforums.org/showpost.php?p=121355&postcount=5")

If you want to use the Live CD and want to put the GRUB on the MBR *over* the WinXP bootloader, then follow this post

[Ubuntu Forums - HOWTO: Restore GRUB - Post #2]("http://ubuntuforums.org/showpost.php?p=117829&postcount=2")

---

### Post by towsonu2003 on 2006-02-06
hey very nice post! updated the wiki with this info - thanks!

---

### Post by Sutekh on 2006-02-06
Hey that's cool!  How did you do that? :-k 

(I'm a wiki n00b! )

---

### Post by towsonu2003 on 2006-02-07
[QUOTE=Sutekh]Hey that's cool!  How did you do that? :-k 

(I'm a wiki n00b! )[/QUOTE]
well, basically, copy paste + giving references :twisted: 

I'm a wiki format newbie myself eheh \\:D/ 

to edit the ubuntu wiki pages, you can go to [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/) , register or login, than go to a page you wanna edit, and choose edit. Once you're done, you can see a preview, attach a note (of what you did), and post (and optionally subscribe to) it. That's all.

---

### Post by pranav on 2006-02-07
Thank you all for your quick responses.
I am typing through Ubuntu now. 
The Install CD method worked for me. Just need to be careful abt the  "Do not format option"
Didnt have to try the Live CD.
Once again a BIG thank you.
The Open Source and Free Software Community rocks.
Lots of love to you all.

---

