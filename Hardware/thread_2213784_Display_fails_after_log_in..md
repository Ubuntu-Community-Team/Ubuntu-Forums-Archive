---
title: "Display fails after log in."
date: 2014-03-28
forum: Hardware
---

### Post by robbiejormerod on 2014-03-28
I have a GeForce 8600GT card on a PCI Express slot that died on me today. I have removed it and hooked up my monitor to the on board graphic port. Everything is fine until I log in then the screen goes blank and all I get is the cursor which I can move about but that is it. I'm guessing that it is something to do with the settings trying to detect the defunked graphics card. I can load up from a live USB and access the hard drive but I have no clue where to go to reset things to try and get the on board graphics working properly. Any help would be very welcome as things are running soooooooooo slow from this live USB. Oh I is using 13.10  by the way.:(

---

### Post by Navneet_Kumar on 2014-03-28
I think the desktop managers config files have been corrupted or deleted by mistake........press ctrl+F2.....to start the terminal and then start compiz/unity/gnome-control-center....whichever applcable.....it might solve the problem......

---

### Post by GigabyteProduction on 2014-03-28
Well if everything is okay before you login, then i think it should be a user-specific thing (your display settings are per-user). You could try going into a virtual teminal before logging in with ctrl+alt+(one of f1-f6), login there, and get rid of the settings files for display in your /home/USERNAME_HERE folder. Since i use Xubuntu instead of Ubuntu, i use xfce instead of gnome and unity stuff so i don't know what the setting file is going to be called, but it should have a name that's relevant and be inside ~/.config.

---

### Post by robbiejormerod on 2014-03-29
Still stuck with this one. If I try and start compiz or gnome I get Fatal: couldn't open display. Unity gives no display variable set. I have no idea which setting files to delete. Any further ideas welcome.

---

### Post by robbiejormerod on 2014-04-13
I ran check and repair on the HDD from a live disk
Sudo e2fck -cf /dev/sd** 
where **is the drive letter and partition number
Then went back to using the open source driver, it seems to be fine now.

---

