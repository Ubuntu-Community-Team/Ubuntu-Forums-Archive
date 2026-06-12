---
title: "Triple boot Windows, Ubuntu, Sabayon"
date: 2007-02-18
forum: Gentoo and derivatives
---

### Post by FuturePilot on 2007-02-18
Is this possible? If so how would I do this? I've decided to give Sabayon another chance after the disaster with my laptop:shock: But this time I'm going to try it on my PC. With a few issues with Ubuntu that are really starting to annoy me I tried the Sabayon live CD to see if my problems still existed. So far I'm pretty impressed. But I'm not a big fan of KDE. I don't like the fake transparencies. IMO if you can't do true transparencies (i.e Beryl) don't do them at all. And I don't like the huge crowded menus. I really liked the way Ubuntu has everything laid out in a neat order. But I'm willing to give it all a try. So can it be done?

---

### Post by rsambuca on 2007-02-18
Easy.  I assume from the sounds of things you already have XP and ubuntu installed?  Basically just partition your drive, stick in the Sabayon DVD or CD, and install it onto another partition.  Sabayon uses grub, although I can't remember off hand whether it recoginzed ubuntu or not.  If it doesn't, just edit your menu.lst to have the choice between XP, ubuntu, or Sabayon at bootup.  (I have XP, Vista, ubuntu, ubuntu 64bit, Sabayon all installed, it is actually quite easy)

If you need assistance, just post here.

---

### Post by solar george on 2007-02-18
Yes it can. (in theory)

The ubuntu installer should automatically detect previously installed OSs and set up the boot menu. So install the other two first, then ubuntu

---

### Post by FuturePilot on 2007-02-18
When I tried a dual boot on my laptop with Ubuntu already installed Grub no longer recognized Ubuntu, I only had Sabayon listed. So how do get all the OSes recognized?

---

### Post by solar george on 2007-02-18
If you install ubuntu last it will recognise the other OSs. If you already have ubuntu install and want to add sabayon post back.

---

### Post by rsambuca on 2007-02-18
There are two methods you can use to modify your system:  You can edit the menu.lst from your sabayon partition to add the ubuntu info, or you can re-install the ubuntu grub loader (which you may have to add Sabayon to anyways.)

---

### Post by FuturePilot on 2007-02-18
I've already got Ubuntu installed but when I install Sabayon I'll lose Ubuntu from Grub. So how would I edit the list?

---

### Post by rsambuca on 2007-02-18
Since you will be in Sabayon,  just enter a terminal as root user.  Enter your password, and then edit your menu.lst using the text editor.  ie. ```
kate /boot/grub/menu.lst
```
You will then see Sabayon's grub listings.

I would then open another terminal, and open up the menu.lst file from your ubuntu partition.  Then just copy and paste the ubuntu load info into the Sabayon grub loader.

ie. the part that says:  Title.... root... kernel... initrd...

Save and reboot.  It will show up in the grub as a choice next bootup.

---

### Post by RAV TUX on 2007-02-18
> **FuturePilot said:**
> I tried the Sabayon live CD to see if my problems still existed. So far I'm pretty impressed. But I'm not a big fan of KDE. 

If you don't like KDE Sabayon is perfect for you since the DVD install comes not only with KDE, but also Gnome, XFCE, Fluxbox and E16 by default...easy if you don't like KDE simply don't use it.

---

### Post by FuturePilot on 2007-02-19
> **RAV TUX said:**
> If you don't like KDE Sabayon is perfect for you since the DVD install comes not only with KDE, but also Gnome, XFCE, Fluxbox and E16 by default...easy if you don't like KDE simply don't use it.
Wow! I didn't know that! Thanks. Right now I have the mini version, but I might go get the DVD now:)

---

### Post by RAV TUX on 2007-02-19
> **FuturePilot said:**
> Wow! I didn't know that! Thanks. Right now I have the mini version, but I might go get the DVD now:)

download Sabayon 3.26 DVD from linuxtracker it is the most up to date one I use.

found here:
Sabayon Linux x86 3.26 DVD
[http://linuxtracker.org/torrents-details.php?id=3406](http://linuxtracker.org/torrents-details.php?id=3406)

and here:


Sabayon Linux x86-64 3.26 DVD
[http://linuxtracker.org/torrents-details.php?id=3407](http://linuxtracker.org/torrents-details.php?id=3407)

---

### Post by FuturePilot on 2007-02-19
Thanks again! 
Downloading now:popcorn:
Is Bittorrent supposed to be this slow? I've got 35 seeds but I'm only getting 10KB/s:confused:
Never mind. Much faster in Ubuntu.:razz:

---

### Post by Zyren on 2007-02-20
I installed sabayon when i already had ubuntu installed and the new grub install just had sabayon on it. I followed one of the guides posted earlier in this thread to view ubuntu's menu.lst in the grub folder and i copied the code for ubuntu in regular and safe mode.

When grub loads and i try to start ubuntu is says "error 15: file not found" When i try starting it in safe mode it loads fine. When i "exit" out of safe mode the login screen for the regular ubuntu comes up and i can log in properly without a problem. Why do i get the error 15?

---

### Post by remick182 on 2007-02-23
I tried to copy and paste the info from my Ubuntu /boot/grub/menu.lst file into my Sabayon /boot/grub/menu.lst, but I keep getting an "Error 13: unrecognizable format or executable" or something like that upon selecting "Ubuntu" at the GRUB loader.

I then tried using supergrub that I found here: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) but I can't figure out to replace or rewrite my GRUB loader.  I have Edgy right now, but I have older versions of Ubuntu on CD (Dapper I believe).  I've heard that it is best to install Ubuntu after Sabayon, but since the damage is already done, what would be the easiest way to repair GRUB through Ubuntu so that all my OS's are bootable?  (I have Ubuntu and XP on master HD, ans Sabayon on slave drive)

---

### Post by confused57 on 2007-02-23
> **remick182 said:**
> I tried to copy and paste the info from my Ubuntu /boot/grub/menu.lst file into my Sabayon /boot/grub/menu.lst, but I keep getting an "Error 13: unrecognizable format or executable" or something like that upon selecting "Ubuntu" at the GRUB loader.

I then tried using supergrub that I found here: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) but I can't figure out to replace or rewrite my GRUB loader.  I have Edgy right now, but I have older versions of Ubuntu on CD (Dapper I believe).  I've heard that it is best to install Ubuntu after Sabayon, but since the damage is already done, what would be the easiest way to repair GRUB through Ubuntu so that all my OS's are bootable?  (I have Ubuntu and XP on master HD, ans Sabayon on slave drive)

You could use the(any) live cd to reinstall Ubuntu's grub to the mbr:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Also, you could install Sabayon's grub to Sabayon's root partition, then add an entry to Ubuntu's grub to boot by chainloading, e.g.:
title   Sabayon
rootnoverify (hd1,0)
chainloader +1

---

### Post by rsambuca on 2007-02-23
I just copied portions of my ubuntu grub menu.lst into the Sabayon and it didn't work until I took out some of the lines.  Just copy the title, root, kernel, and initrd lines, and forget about the rest (quiet, savedefault, boot, etc.).  I have no idea why, but that worked for me.

---

### Post by FuturePilot on 2007-02-23
I finally got around to installing but Windows is gone from Grub. How do I get Windows back? Not that I use that much anymore:p

---

### Post by RAV TUX on 2007-02-24
> **FuturePilot said:**
> I finally got around to installing but Windows is gone from Grub. How do I get Windows back? Not that I use that much anymore:p
which version XP or Vista?

---

### Post by zaratustra on 2007-02-24
> **FuturePilot said:**
> I finally got around to installing but Windows is gone from Grub. How do I get Windows back? Not that I use that much anymore:pWhy the hell you want it back?!:lolflag:  You just manually add it to /boot/grub/menu.lst, there is a zillion howto's on that issue

---

### Post by FuturePilot on 2007-02-25
It's XP

---

### Post by david2007 on 2007-09-10
i tried to reinstall sabayon and then Ubuntu .. But ubuntu doesnt recognize the Sabayon OS. I tried to reinstall two times , having ubuntu always at last , changing just partitions .. What else i neeed to look ? Maybe the advance settings in the grub installation ? 
Changing just the grub from Ubuntu didnt worked :confused:

---

### Post by confused57 on 2007-09-10
> **david2007 said:**
> i tried to reinstall sabayon and then Ubuntu .. But ubuntu doesnt recognize the Sabayon OS. I tried to reinstall two times , having ubuntu always at last , changing just partitions .. What else i neeed to look ? Maybe the advance settings in the grub installation ? 
Changing just the grub from Ubuntu didnt worked :confused:

Boot into Ubuntu, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
-l is a lowercase "L"
This will show your partitions, especially where Sabayon is installed.

Then add an entry to your menu.lst to boot Sabayon:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Then add a configfile entry to boot Sabayon at the very end of your Ubuntu menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)

Sabayon uses grub.conf, instead of menu.lst, so you entry would be something like this if Sabayon is on the first partition:

```
title   Sabayon
configfile  (hd0,0)/boot/grub/grub.conf
```

You might want to copy&paste the commands into a terminal.

---

### Post by rsambuca on 2007-09-10
That should work very well.  An alternative would be to use the chainloader command.```
title     Sabayon
root      (hd0,0)
chainloader +1
```

---

### Post by david2007 on 2007-09-10
thanx alot confused57 for your useful information..and rsambuca also :)
i finally get it running :guitar:

---

