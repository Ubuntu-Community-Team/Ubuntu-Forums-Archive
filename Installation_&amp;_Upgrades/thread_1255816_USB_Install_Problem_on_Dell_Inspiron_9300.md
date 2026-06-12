---
title: "USB Install Problem on Dell Inspiron 9300"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by Andrew360 on 2009-09-01
I'm having a problem with Ubuntu 9.04 on a Dell Inspiron 9300.

The optical drive is picky, so I used UNetbootin to create a bootable flash drive using an ISO I downloaded from Ubuntu.com.

When I boot to the drive it just starts loading the live version. No questions asked, no prompt to install. In the past I have tried the live cd and it gave me options... anyway.

It boots up, looks fine to me, auto logs in, at the desktop the background image looks stretched. (Don't know if that is related to this issue. Everything else appears correctly, at native resolution.)

If I don't touch anything, it'll sit there for a while.

If I do click anything, anything at all, it flashes a black screen with some white text on it. I can't actually tell what it says becuase it happens so quickly. I'm pretty sure a screen cap is out of the question. It then goes back to the login screen and automaticly logs in again. Repeat.

I haven't done very much with Linux yet, so your insight is greatly appreciated.

---

### Post by presence1960 on 2009-09-02
Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso prior to creating the USB?

If the hashes don't match exactly your iso is corrupted.

If the hashes match exactly try recreating the bootable USB.

Try "check disk for defects" option when it loads. if it passes try to install.

If the same thing happens look [here]("https://help.ubuntu.com/community/BootOptions"). You may want to look at F4 safe graphics mode.

If all else fails try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by Andrew360 on 2009-09-20
I did check the MD5SUM and it matched.

It looks like Unetbootin does something to bypass the screen where you can select safe graphics mode. I did try redoing the flash drive, but I had the same problem.

Are there any other methods to boot from a flash drive (that don't involve Ubuntu already being installed)?

---

### Post by presence1960 on 2009-09-20
> **Andrew360 said:**
> I did check the MD5SUM and it matched.

It looks like Unetbootin does something to bypass the screen where you can select safe graphics mode. I did try redoing the flash drive, but I had the same problem.

Are there any other methods to boot from a flash drive (that don't involve Ubuntu already being installed)?

when you boot off the flash drive don't use default choose one of the other options.

---

### Post by Andrew360 on 2009-09-20
My other options are Help and OEM. If I use the OEM option it ends up in a BusyBox CLI. Not quite what I had in mind. :)

It will let me press tab for install options. Is there something I can add to this to make the install easier?

---

### Post by presence1960 on 2009-09-20
> **Andrew360 said:**
> My other options are Help and OEM. If I use the OEM option it ends up in a BusyBox CLI. Not quite what I had in mind. :)

It will let me press tab for install options. Is there something I can add to this to make the install easier?

I never used unetbootin to install ubuntu. But I did use it to install sabayon 4.1. When I boot the flash drive there are options for default (unetbootin) and then all the sabayon Live Cd options. 

I also have gparted Live CD on a flash disk and it is the same thing. I have the options default (unetbootin) then all the gparted Live CD options.

I never use default (unetbootin) options. I always choose the options of sabayon or gparted Live Cd.

If you do not have default then the ubuntu Live CD options such as "try ubuntu without any changes", "check disk for defects", "install ubuntu", etc - which is where those F4 and F6 options are then I would say you have a bad flash disk "burn".

---

### Post by Andrew360 on 2009-09-20
I have some good news and some bad news. Following the instructions here [https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu) USB desktop image creator I was able to get back part of the menu. I does let me choose from some of the options, but no F4. :(

I did check the install media for errors and none were found.

Any other ideas?

---

### Post by presence1960 on 2009-09-20
> **Andrew360 said:**
> I have some good news and some bad news. Following the instructions here [https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu) USB desktop image creator I was able to get back part of the menu. I does let me choose from some of the options, but no F4. :(

I did check the install media for errors and none were found.

Any other ideas?
if you can not get to the screen posted below with all those options available then something is not right with the image on the flash disk.

---

### Post by Andrew360 on 2009-09-20
The image worked fine on a virtual machine. I tried the flash drive in a desktop computer and it ran fine.

I was able to see that screen after making those modifications I talked about in the last post. The fonts were different and there was no list of F keys at the bottom.

When I boot to an ISO from a VM it all looks fine. It must be something about unetbootin....

---

### Post by presence1960 on 2009-09-20
strange to say the least!

---

### Post by Andrew360 on 2009-09-20
I'm not totally surprised. Of course, I'd run into some stupid laptop hardware issue. :)

However one good thing happened... I found out that Linux drivers exist for an old HP printer I have, so tomorrow I'm going to turn the desktop I mentioned into a Ubuntu print server.

---

### Post by presence1960 on 2009-09-20
> **Andrew360 said:**
> I'm not totally surprised. Of course, I'd run into some stupid laptop hardware issue. :)

However one good thing happened... I found out that Linux drivers exist for an old HP printer I have, so tomorrow I'm going to turn the desktop I mentioned into a Ubuntu print server.

lappies can be a pain in the ... because of hardware.

---

### Post by Andrew360 on 2009-09-20
Update: I was able to log on and it stayed good long enough for me to connect to my wireless network.

Then, when I tried to launch Firefox it went back to the black screen with white text. It doesn't look like what I thought a kernel panic would be. I was able to quickly read something about Advanced Power Settings on the last line. Then it went back to the login screen. It will log on to the desktop again, and repeat.

Where the desktop background should be it looks like the top menu bar (whats the official name again?) is stretched. I can kind of see the Ubuntu and Firefox logos. It's weird because the menus and windows look fine, and they're displaying at native resolution. Maybe it's unrelated.

---

