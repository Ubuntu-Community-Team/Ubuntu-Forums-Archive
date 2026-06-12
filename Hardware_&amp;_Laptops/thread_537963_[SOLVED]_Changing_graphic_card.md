---
title: "[SOLVED] Changing graphic card"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by Chikitulfo on 2007-08-29
Hi,
I don't know if this is the right forums for this...

Anyway, I've got a Nvidia Geforce 440 Mx, which is a bit(only a bit) old, so I bought on eBay an ATI Radeon 9600 which was really cheap, and a good one.
But unfortunately i didn't think about its Ubuntu support (I was only thikning about playing some games on my "win-tendo"). And now that I already have it I'm reading that can be really hard to make it run properly.
Anyway, once I have it, I'll use it, the point is that I need some help to uninstall the nvidia drivers from ubuntu, since i have no idea how to do it. (I already removed beryl from the startup programs)

Thanks in advance,
chikitulfo

---

### Post by ajgreeny on 2007-08-29
Before you install the new card, and with ubuntu running, change the driver using **sudo dpkg-reconfigure xserver-xorg**
in terminal.  When you get to the graphic driver part, chose **ati** for the moment, for the rest use the defaults.  At the end of this you can shutdown and install the new card.

Now reboot and the ati 9600 should work fine with this open source driver for most purposes.  

Once you have changed the driver don't boot again before changing the card as the new driver will not run your old card and you'll have to do everything in terminal; possible but not what most people want.

You are correct that it can be difficult to install the ati proprietary driver, I have tried a few times for my 9200 card without success, though I did get it working with a previous version of ubuntu (probably 5.10, but I can't remember).  You can always try, though, but keep a copy of your working ati version of /etc/X11/xorg.conf before you try anything and then you can always revert if necessary.

---

### Post by Chikitulfo on 2007-08-30
Hi, 
when I type sudo *dkpg-reconfigure xserver-xorg* in terminal I get this:
[I]chikitulfo@Chikitulfland:~$ sudo dkpg-reconfigure xserver-xorg
Password:
sudo: dkpg-reconfigure: command not found
[/I]

what should I do to solve it?

---

### Post by ajgreeny on 2007-08-30
*sudo **dpkg**-reconfigure* etc etc, not *sudo **dkpg*** as you used.  Try again.

---

### Post by Chikitulfo on 2007-08-30
Hi,
it was a silly mistake, I did it, but the graphic card isn't working properly (it's broken, it doesn't work properly in windows either...), so i want go back to the previous configuration.

How do i do to replace one file for other in the terminal? (i know where the backup is)

EDIT: ok i managed to do it, thanks for everyhting

---

### Post by ajgreeny on 2007-08-30
**sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nogood**
this will rename your edited **xorg.conf** as **xorg.conf.nogood**
You don't have to do this but it is good practice on cli use and may help you remember the command **mv** better than just hearing it somewhere.

Now copy the old version of xorg.conf back.  How you do this depends on whether you just copied it as a backup in the original place or moved it somewhere else in your file system.

If you just did a backup do:-
**sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf**(change the backup file name in this command to your own backup name)

If you moved the file to another place, eg /home/username do:-
sudo cp /home/username/xorg.conf /etc/X11/xorg.conf

Now go back to your old card if you haven't already done so, and then reboot or even try reseting X with Ctrl+Alt+Backspace if it's already in place.

I hope it all works for you.

---

### Post by Chikitulfo on 2007-08-30
I did it just before you posted, but thanks for everything

---

