---
title: "Problem with SigmaTel 9200 (ATI HDA SB450) [With Solution]"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by MASTERfoil on 2008-01-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/134351](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/134351) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I used the following fix on my Gateway ML3109 laptop immediately after installing Gutsy Gibbon 7.10 because my sound didn't work at all. You should check the launchpad link at the top of this post to see if your problem is similar.

I had read several of the help articles about the SB450 HDA chipset on the Ubuntu forums but nothing seemed to work. I then stumbled upon an article which suggested downloading the latest version of ALSA, patching the snd-hda-intel module to fix a bug which was causing the sound to malfunction, and then compiling/installing ALSA using the downloaded source.

The instructions are as follows.

1) Run this command to get the appropriate development files for compiling ```
sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`
```

2) Download these files :
    [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
    [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2)
    [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)

3) From the download directory run this command: ```
sudo mkdir /usr/src/alsa/ && sudo cp alsa-* /usr/src/alsa/ && cd /usr/src/alsa && sudo tar xjf alsa-driver-1.0.15.tar.bz2 && sudo tar xjf alsa-utils-1.0.15.tar.bz2 && sudo tar xjf alsa-lib-1.0.15.tar.bz2
```

4) Download the patch from this link: [https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2229&type=bug](https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2229&type=bug)

5) From the download directory run the command ```
sudo patch /usr/src/alsa/alsa-driver-1.0.15/alsa-kernel/pci/hda/patch_sigmatel.c < patch_sigmatel.c.patch-1.0.15rc1-simple
``` 

6) Now run this command to compile and install. ```
cd /usr/src/alsa/alsa-lib-1.0.15/ && sudo ./configure && sudo make && sudo make install && cd ../alsa-utils-1.0.15/ && sudo ./configure && sudo make && sudo make install && cd ../alsa-driver-1.0.15/ && sudo ./configure && sudo make && sudo make install
```

7) Open /etc/modprobe.d/alsa-base as root and add the line "options snd-hda-intel model=STAC9200" at the end of the file.

8) Now restart ALSA and unmute your sound.```
sudo /etc/init.d/alsasound restart && alsamixer
```

Let me know if this works for you.

**_UPDATE 1/27/08_**

In following my own instructions on a subsequent install of the distribution Parsix, I found that I was missing a necessary step. Before restarting ALSA, it is necessary to modify /etc/modprobe.d/alsa-base. This is now covered in step 7 of the instructions.

---

### Post by DeathGrind on 2008-01-22
Cool.  Thanks man.  Worked for my Gateway MT3423.  Awesome got sound NOW!!  THANKS!

---

### Post by MASTERfoil on 2008-01-23
**Problem with downloading alsa:**

When downloading the patch, you may have to click the link, log in as a guest, and then click the link again.

---

### Post by th3t1nm4n on 2008-01-23
Can I see the contents of your /etc/modprobe.d/alsa-base and the output you get from sudo lshw -C multimedia ?
I'm trying to figure out if this thread would affect me.
( [http://ubuntuforums.org/showthread.php?p=4194828](http://ubuntuforums.org/showthread.php?p=4194828) )

---

### Post by badarsenewb on 2008-01-24
The instructions worked fantastically me with only one exception. After installing everything I found that I couldn't restart my drivers or get them loaded period. Fixed this by simply going on to root in the terminal and runing alsaconf. After that I could use alsamixer again with no problem and the correct configuration (go figure, lol) for my sound card. Thanks a ton MASTERfoil, can't tell you how long I've spent looking for a solution to this problem.
P.S. I'm using dapper 6.06 and didnt have any issues of the system not being as up to date as the drivers :)

---

