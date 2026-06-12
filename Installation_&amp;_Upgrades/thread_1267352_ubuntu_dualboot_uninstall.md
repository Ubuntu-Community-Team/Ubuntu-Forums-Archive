---
title: "ubuntu dualboot uninstall"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by jbouxa on 2009-09-15
Hello, I installed ubuntu on a dual boot machine with XP not realizing that i installed it on my C drive along side windows. i would like to uninstall and reinstall it on a seperate partition. all help is appreciated.

---

### Post by earthpigg on 2009-09-15
if you installed via [wubi]("http://en.wikipedia.org/wiki/Wubi_%28installer%29"), then you can uninstall ubuntu in the windows add/remove programs.

---

### Post by jbouxa on 2009-09-15
i didn't, i installed it from a live cd session

---

### Post by jbouxa on 2009-09-15
i thought that i could just try reinstalling it on the perferred partition, but then what would i do about the existing install on my c drive

---

### Post by raymondh on 2009-09-15
> **jbouxa said:**
> Hello, I installed ubuntu on a dual boot machine with XP not realizing that** i installed it on my C drive along side windows.** i would like to uninstall and reinstall it on a seperate partition. all help is appreciated.

The above in bold can be confusing.  Installing Ubuntu in C: drive usually means that you installed via WUBI (or as a file within windows) because Ubuntu/linux does not identify using letters (C: drive, D; drive, etc)  but rather sda1, sda2, etc. .  

In post 3  you hinted that you installed it otherwise.... so am assuming you installed Ubuntu in it's own partition.  By the way, a wubi install also uses the liveCD.  What happens is that you have windows operating when you put in the liveCD.

If my assumption is correct, then you have a true dual boot and maybe you just want to move Ubuntu to ANOTHER partition (or HD).

1.  You can use gparted from the liveCD to delete said partition.
2.  You will have to fix the bootloader of window (fixMBR) or .....
3.  Go ahead and install Ubuntu in the preferred partition and let GRUB (the ubuntu bootloader) auto install itself again.

Personally, I would rather fix the windows bootloader first (using an original XP install disc ... not the recovery disc provided by some OEMs) and then re-install Ubuntu.  My reasoning is that if the re-install misfires' during the installation part and I have to cancel out,  at least I have a working windows.  Nevrtheless, either way will work.

Now, if you have a WUBI-installed ubuntu,  you

1.  Boot into windows and access add/remove from control panel
2.  Remove Ubuntu
3.  Access your boot.ini file and manually edit/remove the wubi-related line.  ONLY THE WUBI RELATED LINE.  [See this link for guidance]("https://wiki.ubuntu.com/WubiGuide%C2%A0").

If you are not sure whether you have a WUBI install or Ubuntu-actually-in-its'-own-partition ...... from Ubuntu, access a terminal (applications > accessories), type and post back the results of

```
sudo fdisk -l
```

small L, not I nor 1

Back-up your files. There are ZERO guarantees when doing partition work.

---

### Post by jbouxa on 2009-09-15
to raymond henson, you're right, that was confusing, sorry. i did install it without the wubi installer though. i know so because i couldn't remove it from the ADD/REMOVE menu.

---

### Post by raymondh on 2009-09-15
> **jbouxa said:**
> to raymond henson, you're right, that was confusing, sorry. i did install it without the wubi installer though. i know so because i couldn't remove it from the ADD/REMOVE menu.

Jbouxa,

No worries.  Let's move on.  can you access a terminal, type and post back (copy/paste) the results of

```
sudo fdisk -l
```

Let's get a picture of your HD and maybe we can write a tutorial on how to move Ubuntu and to where.

Back-up your personal files.  Also, do you have a windows original install disc or a recovery disc (spupplied by the manufacturer)?

Also, you may want to consider this alternative.  Note I have not done it ... preferring to do it manually.

[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

---

