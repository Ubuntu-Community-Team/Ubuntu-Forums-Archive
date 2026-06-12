---
title: "Problem with installation"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by linid0t on 2009-10-03
I'm trying to install the ubuntu netbook remix onto my Asus EEEpc 900HA.
I'm currently using Windows XP.
I downloaded the file, and followed the guide here:
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)
to set up everything.
However, after writing the IMG file onto my USB stick, nothing happens.
The computer reads the USB stick as "Install Ubuntu Netbook Remix", it contains an application called "wubi".
After selecting wubi, nothing happens.
Sorry if this problem seems really simple, I'm new to all this stuff.

---

### Post by raymondh on 2009-10-03
> **linid0t said:**
> I'm trying to install the ubuntu netbook remix onto my Asus EEEpc 900HA.
I'm currently using Windows XP.
I downloaded the file, and followed the guide here:
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)
to set up everything.
However, after writing the IMG file onto my USB stick, nothing happens.
The computer reads the USB stick as "Install Ubuntu Netbook Remix", it contains an application called "wubi".
After selecting wubi, nothing happens.
Sorry if this problem seems really simple, I'm new to all this stuff.

Hello and welcome.


Are you planning to install "inside windows" (wubi).  That means that you have windows open when you insert the USB drive.  Or, do you want to install UNR in its' own partition?  

Try booting into the USB key....if you want to install in own partition:

-as computer starts' up, pause it to enter BIOS (you should have a F-key or need to press esc)
-select the USB drive to start up first ... ahead of the internal HD
-put USB thumb drive
-proceed with start-up

---

### Post by linid0t on 2009-10-03
Thanks, but now I have a new problem.
Installer starts, I go through everything fine until step 4.
I choose to specify partitions manually.
I've already set up a 40GB partition, labeled here as "unusable".
I select it, then click forward.
I get the error "No root file system".
How can I fix this?

---

### Post by gadolinio on 2009-10-03
I would boot with the usb stick, and then open system--administration--gparted partition editor to format the partition where you want to install ubuntu in ext3.  And then tell the installer to use that partition. It worked fine in my desktop.

---

### Post by oneshot22 on 2009-10-03
I can't get ubuntu to load after I install it. there is an error "C: boot.ini." Then it boots into Windows. So I don't know what to do? Can anyone help?:confused:

---

### Post by raymondh on 2009-10-03
> **oneshot22 said:**
> I can't get ubuntu to load after I install it. there is an error "C: boot.ini." Then it boots into Windows. So I don't know what to do? Can anyone help?:confused:

You seem to have the wubi-installed ubuntu.

Have you tried this?

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

Run checkdisk from windows.

---

### Post by linid0t on 2009-10-04
Thanks, but now I have a new problem.
I managed to install it, and was fiddling around with the options.
Decided to change the appearance, I changed it so it looked like the desktop version instead of the netbook one.
Now when I boot up, all I get is my background pic.
I can right click the picture, create a folder, and then explore from there, but that's all I can do.
Any way to fix this, or do I just have to delete it and start again?

---

