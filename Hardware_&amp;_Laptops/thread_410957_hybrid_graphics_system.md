---
title: "hybrid graphics system"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by ampanab on 2007-04-16
Hello,
Just wanted to give my 2 cents in.
For those who are using hybrid graphical systems, i.e. 2 graphics card in the same laptop/desktop, ubuntu will fail to find the default graphics card. I have a sony vaio VGN-SZ series that has 2 options of either using the integrated graphics card or the nvidia. If anyone else has problems with  booting up and xserver failed to find the default graphics then it will most likely be that either graphics card was switched. Anyways, that's pretty much it.

---

### Post by dubrict on 2007-04-16
In your xorg.conf file, you need to specifiy the PCI Bus ID of the graphics card you want to use.  Under the device section for the graphics card, put:

BusID  "PCI:0:0:1"

Or whatever the bus location of the card you want is.  Also make sure the right driver is chosen.

If somebody else would like to elaborate on this, feel free.
 I think it would be really great to see better x configuration in ubuntu.  I get pissed off about how it still sets my max resolution to 1024x768 even after 3 or 4 new versions of the OS, and I always have to enter it manually into the file.

---

### Post by edarroyo on 2007-04-17
yeah, i get that a lot... is there a way to work around this? because i hate it! i installed ubuntu while being the "speed" mode which uses the nvidia graphics card. so now if i try to switch to "stamina" mode which uses the intregrated intel graphics card... i get that error... is there a way to not get this error at all ?

---

### Post by hihihi on 2007-04-28
hello,

me too. running ubuntu feisty on a laptop with two graphic cards.
intel 915g-bla and bla-fx nvidia 6600 go. which is good. 
i've chosen nvidia as my favorite due to my general needs.
intel is very handy on battery-mode. i get about 1h longer battery live.

what i do now to have a quick setup when switching to intel:

-i made a xorg.conf for each card and saved them as a backup-xorg.conf under /etc/X11/ where the xorg.conf resides. i named them xorg.conf.intel and xorg.conf.nvidia.

when i want to shutdown in order to switch the graphic card to intel, i launch before that the terminal and type in:

$ sudo cp /etc/X11/xorg.conf.intel /etc/X11/xorg.conf

thats it. if you configured the card and its xorg.conf right this works fine.

Another way to do that, for example, you wake up and coffee is cooking and your spontaneous enough to switch over to intel without step explaned before, do the following:
a) let your maschine start up.
b) get a cup of coffee.
c) let the xserver crash and moan your favorite morning-slogan
d) xserver shows a blue screen with the warnings and questions. go through it till screen turns to black and white text mode.
e) sometimes it asks you now for login --> login
if not: press ctrl+alt+F1 and login
f) $ sudo /etc/init.d/gdm stop
g) $ sudo cp /etc/X11/xorg.conf.intel /etc/X11/xorg.conf
h) $ sudo /etc/init.d/gdm start

and voila, works fine!

i'm thinking of writing a script that does this automatically, but that will take time as my bash skills are bad.

---

### Post by hihihi on 2007-11-23
i had to make the script for my system and now it is WORKING.
great,,,i am very happy now.
i dont have to copy xorgs before restarting on other graphic-card.
AND MOST COOL: OPENGL WORKS ON BOTH CARDS!!


btw:

this should also work on a  sony vaio with stamina mode, mine is another laptop (alienware / uniwill / jewel) with an intel915g and nvidia go6600
AND i installed FIRST nvidia full enabled and afterwards i did this here:



here is how i did it (beware that most paths in the script bellow are adapted to my own enviroment, find them and replace them [like libglx]):

-- write a boot-script // graphic-card recognition on boot-up // :

1.) first of all i wrote two xorg.conf files:
one for nvidia, i called it xnvidia
one for intel, i called it xintel
and saved them in my home directory (/home/jo/)

2.) than i created an "intel"-folder under /usr/lib/xorg/modules/extensions/
sudo mkdir /usr/lib/xorg/modules/extensions/intel

3.) than i copied the exixting libglx.so in /usr/lib/xorg/modules/extensions/ to /usr/lib/xorg/modules/extensions/intel and renamed it to libglx.so.intel
sudo cp /usr/lib/xorg/modules/extensions/libglx.so /usr/lib/xorg/modules/extensions/intel/
sudo mv /usr/lib/xorg/modules/extensions/intel/libglx.so /usr/lib/xorg/modules/extensions/intel/libglx.so.i ntel

4.) now we need the missing libgl.so.1.2
go to this site: [http://packages.ubuntu.com/feisty/libs/libgl1-mesa-dri](http://packages.ubuntu.com/feisty/libs/libgl1-mesa-dri) and download the package (not with the package-manager, just download it to your home directory)

5.) afterwards go to your /home/wherever/libgl1-mesa-glx_6.5.2-3ubuntu7_i386.deb and RIGHT-CLICK with the mouse, open with archive-manager:
you will see two tar.gz files: dubble-click on the data.tar.gz, dubble-click on the /. folder, dubble-click on the /usr folder and extract the libgl.so.1.2 file to your /home/wherever directory

6.) now copy this libgl.so.1.2 to the intel folder in /usr/lib/xorg/modules/extensions
sudo cp /home/wherever/libgl.so.1.2 /usr/lib/xorg/modules/extensions/intel


7.) lets write the boot script to auto recognize the graphic-card

sudo gedit /etc/init.d/vaio (paste the text below)

#!/bin/bash

##switch between stamina and speed mode

VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then

cp -f /home/jo/xnvidia /etc/X11/xorg.conf

ln -sf /usr/lib/xorg/modules/libglx.so.1.0.9639 /usr/lib/xorg/modules/libglx.so

ln -sf /usr/lib/libGL.so.1.0.9639 /usr/lib/libGL.so.1

else

cp -f /home/jo/xintel /etc/X11/xorg.conf

ln -sf /usr/lib/xorg/modules/extensions/intel/libglx.so.i ntel /usr/lib/xorg/modules/libglx.so

ln -sf /usr/lib/xorg/modules/extensions/intel/libGL.so.1. 2 /usr/lib/libGL.so.1

fi


8.) sudo chmod 755 /etc/init.d/vaio
9.) sudo ln -s /etc/inid.d/vaio /etc/rc2.d/S12vaio

THATS IT, REBOOT, BE HAPPY,
HAVE FUN,
THANKS TO SHELTERED
__________________

---

