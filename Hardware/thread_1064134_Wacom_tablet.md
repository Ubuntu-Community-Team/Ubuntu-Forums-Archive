---
title: "Wacom tablet"
date: 2009-02-08
forum: Hardware
---

### Post by Nemix on 2009-02-08
i got myself a wacom bamboo fun tablet, i went with wacom cos i knew they had drivers for Linux. ok so i got home and plugged it in i could move the cursor around and all after that i think i screwed up...
so i thought to myself let me just make sure i got all the drivers and such. went onto their website got the link where i can go to find the drivers and started the process of getting it all up, then i saw that cos my tablet is a usb device i might not need to do this installation process... and now nothing happens when i move the pen.

these are the step i did:
download the package then
    $ bunzip2 linuxwacom.tar.bz2
    $ tar xvf linuxwacom.tar
    $ cd linuxwacom/prebuilt
    $ su
    # ./uninstall
    # ./install
    # cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
    # gedit /etc/X11/xorg.conf
    # reboot

sudo instead of su basically
these steps are from the README file on the drivers file that i downloaded. im still not all that great with how unix like systems work so some of the steps up there i dont even know what i did:(

---

### Post by ragtag on 2009-02-08
Wacom can be a little tricky on Linux, but it works fine once you have it set up.

Check out [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) for detailed instructions.

In 8.10, Ubuntu switched to using HID instead of xorg for the wacom. This makes it possible to plug in and out the tablet, but you loose some configuration options you had with xorg. The page above explains it all.

Btw. you shouldn't need to download any external packages to use your wacom on Ubuntu. All you need is in the software repository. Just open the synaptic package manager and search for wacom. Also, the next to last step you did is opening a text editor to edit xorg.conf. Did you actually make any changes to that file?

Note! That be careful when editing xorg.conf. Make a backup of it, and make sure you know how to restore the backup without a graphical user interface. (basic command line commands are needed, like sudo, cd, cp, ls etc.).

---

### Post by Nemix on 2009-02-08
thanks for your reply,
i made sure i didnt edit the text file that came up:D

im going to read through that link looks helpful :KS:KS:KS

---

### Post by Nemix on 2009-02-08
umm is it worth doing option B, i do want all the buttons to work and all but not sure if its worth the risk of "you risk hosing X":(

---

### Post by ragtag on 2009-02-09
I've set both my machines to using x. It's not that dangerous.

If you do hose X you get asked a few questions, if you want to see diagnostic and so on. From here you can actually go in and edit your xorg.conf to try and fix the error.

An alternative is to hit Ctrl-Alt-F1. You then get a scary full screen dos like command line you can log into. :)

If you make a copy of your xorg.conf file before you ever touch it (as xorg.conf.backup in your /etc/X11 folder). You can restore it in case you mess it up like so.

```

cd /etc/X11
ls -l
sudo cp xorg.conf.backup xorg.conf

```

The first command goes into the /etc/X11 folder.

The second lists the content of the folder. This is not required, but handy to know what's in the folder. You can also type 'pwd' to see what folder you're in.

The third copys the xorg.conf.backup file over your current xorg.conf file.

It's pretty simple really.

---

