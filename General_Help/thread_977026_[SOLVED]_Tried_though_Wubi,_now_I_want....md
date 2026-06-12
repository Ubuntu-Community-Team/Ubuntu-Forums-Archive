---
title: "[SOLVED] Tried though Wubi, now I want..."
date: 2008-11-09
forum: General Help
---

### Post by cmckee1980 on 2008-11-09
Hi,

I installed the latest Ubuntu within Windows Vista by using Wubi.  I think I'd like to completely blow away Vista now, after just a short week or so, but I'd like to not have to reinstall Ubuntu completely and lose all my nice settings and whatnot that I've already configured. Any ideas on how to do this?

Thanks...

---

### Post by jklslvch on 2008-11-09
Well.. your gonna have to blow Everything away... but you can save your home folder...

while your in ur ubuntu open a console and type
sudo nautilus
   urpasswrd
and a file manager opens up
now go to this location
/home
now youll see a folder there with your user name
right click on it and compress it?? if its that eazy i dont know
and compy the compressed file to a pendrive
now reboot> reinstall
create the same username you had
once its created ..... the only thing i can think of is start the live cd , extract the folder and replace it with the old one on your new install...

that should work permissions and settings and all... im confident of it... at least thats what i would do

---

### Post by cmckee1980 on 2008-11-09
Yes, that does make sense, and it shouldnt be too large after just a weeks worth of customization and whatnot, thanks for the help!

---

### Post by solitaire on 2008-11-09
easy way around this is, If you have an external drive big enough to hold your Home folder uncompressed and it is FAT or NTFS formatted then all you need do is copy your Home folder directly on to thet external drive

So once you have reinstalled Ubuntu all you need to do is copy your Home folder back.

I've done this a few times when replacing hard drives and doing a clean install of a new Ubuntu version :D

Note you'll have to reinstall any programs you had added, but all their settings will still be there in your Home folder.

---

### Post by bodhi.zazen on 2008-11-09
You can convert you wubi to a regular partition, then delete your windows and resize your Ubuntu partition.

To be honest, a fresh installation may be easier :twisted:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
		[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)
		[https://launchpad.net/lvpm](https://launchpad.net/lvpm)

---

### Post by cmckee1980 on 2008-11-09
thank you all... feeling now that a clean install might be easiest, i had a lot of fun setting up Ubuntu in the first place, if things fail, at least ill get to have more fun doing it again :)

---

