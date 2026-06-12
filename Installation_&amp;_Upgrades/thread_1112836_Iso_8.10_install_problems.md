---
title: "Iso 8.10 install problems"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by Snowghost on 2009-04-01
hey guys
first time trying this.

im installing on an old computer Ubuntu 8.10 
the computer has two hard drives, one is partitions to have 30gb for winxp, 10gb free.
the other is about 100gb 25gb used with music and such.
the computer has no cd drive, so im trying via iso

the demo is there and i can access that, but the install on that gets hungup

installing using wubi.exe gets me as far as "creating image" but then i get a windows msg telling me it has to stop. the report on it so huge. will post a picture of that later.


should i be reformating my drive using windows first before installing?

what i can tell you is the msg says:
appname wubi.exe    appver 8.10.0.515.
modname cd2iso.dll   modnum 0.0.0.0
offset 00007ceb



thanks
Snowy

---

### Post by lindsay7 on 2009-04-01
You do not need to format you drive to install with Wubi. Ubuntu installs under Windows with this method.

You should post all the info that you have on your system, including make, model, ram, video card, cpu, ect. It sounds like you may have a hardware conflict.  There may be a way to work around it, but system info is needed.

Is this where you are getting Wubi.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Snowghost on 2009-04-02
my goodness.
ok

the computer is 10 years old. are parts going to be reconisded?
its going to be a mishion to get them.

if i run the demo and run the installer from there i get to the same point (well the translated, ubuntu styled point)


it came with the  8.10 download.....didnt it?


thanks

---

### Post by lindsay7 on 2009-04-02
Try to install from the web site I gave you. Sometimes the disks do not work if they are bad.

---

### Post by Snowghost on 2009-04-03
i tryed the download but same as before

this is a screanshot of what i get. as you can see buy the scrole bar, thats alota code. (i can not slectet it to coppy and paist, sorry)
[IMG]http://i139.photobucket.com/albums/q288/Killargorilla/ubuntuinstallfail1.jpg[/IMG]


is this enough info on my computer?

---

### Post by dtoronto on 2009-04-03
You also might try a USB install if your machine supports it.

---

### Post by lindsay7 on 2009-04-04
Looking at what is on your screen, I can not tell what is going on but it looks like you may have the Install disk in the computer and it shows a drive D:

You need to take the install disk out of the computer and go to the Wubi web site and try the Ubuntu install from there.  It will install on you windows drive. I do not know why there are other drives showing on what you sent from the screen shot. Normally your windows system is on the c: drive.

---

### Post by Snowghost on 2009-04-05
you right, it is on the C drive

am i ment to be installing it to the C drive? (i thoght it wasnt good to have two OSs on the same partishion 
\(D drive is a partishion of the same hard disk)

i tryd the earlyer version of ubuntu but same problem. but i tryd on the D drive and M drives.

i will try C drive then.

---

### Post by lindsay7 on 2009-04-05
Wubi installs under windows, so it will be with you windows drive. You will not see an extra partition. If you want to uninstall it you would do it from the windows from the control panel.

---

### Post by Snowghost on 2009-04-05
ok that might help, il try that.


so can i uninstall windows afterwards to free up my windows OS to put on another computer/

---

### Post by lindsay7 on 2009-04-06
No not exactly. If you install Ubuntu with Wubi in is installed under windows just like another windows program. If you uninstall Windows, Ubuntu will also be uninstalled too.

Are you wanting to have a dual boot system or do you want to just install Ubuntu on this computer and have a Windows system on another computer?

---

### Post by Snowghost on 2009-04-06
the second. id like to install ubuntu, so i can uninstall windows (to use somewere else)

Note
i do not have a cd drive on this computer

---

### Post by lindsay7 on 2009-04-06
Based on what you have said, this is going to be the easiest thing for you to do.

1. Go to the Wubi web site and install Ubuntu under Windows.

2. After you have this done. Look under Systems in the top menu bar and go down to Administartion, USb Sartup disc creator, get a USB stick and do this.

3. You can now install Ubuntu on any comupter that you want with this USB stick. If you want to install Ubuntu and use the full hard drive this will wipe out your Windows system leaving only Ubuntu on that computer. You could also choose to have a dual boot system where both Ubuntu and Windows are on the same hard drime and you choose which system you want to start up.

---

### Post by Snowghost on 2009-04-07
but if i uninstall windows. which wipes everything. will i not lose the driver for the usb ports on my mobo?

---

### Post by lindsay7 on 2009-04-07
NO. The USB port run off of the motherboard before any Operating System Starts Up.  Then the OS might manage them.  If you want to start you computer from a USB bootable drive, you need to get into the Bios and tell it to start up on the USB port first.  Normally the computer is set to start up in this order. 1. cd/dvd drive  2.  Hard Drive  3. usb or other device.  You should search the web and this forum for info on start ups and general information.

---

