---
title: "How to get Sony SZ28 direct rendering to both i945 and nvidia go 7400 in Edgy"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by sheltered on 2007-04-15
First of all, HI EVERYONE~ :D

i'm newbie to ubuntu and linux since i've never used it before (even though i've installed it couple times to see what it's like)

This is also the first time writing the post... so i'm really excited!! haha!

I have this odd Sony SZ28 (YES it's 28!! bought it in korea) laptop which has two graphic cards..

one with i945(??) and one with nvidia go 7400

and i've been struggling to get both of graphic cards to run with direct rendering!
so, I ended up exploring NVIDIA driver package. And finally figured out to solve the problem with symlinks (I know they are ugly and all but this is the best i can do)


*** I have Edgy with kernel 2.6.17-11-generic, and xorg7.2!
*** Boot script for stamina and speed mode is available on: [http://avilella.googlepages.com/vaiosz](http://avilella.googlepages.com/vaiosz)
(I also got my webcam to work)

STEP 0:
  You should get the stamina mode and speed mode sorted out before you start anything



STEP 1:
   Boot with your stamina mode Get i810 driver to work in FULL 3D first!! Since installing Nvidia driver is really easy

STEP 2:
   Copy the following files for GLX!! to some place safe!

/usr/lib/xorg/modules/extensions/libglx.so
/usr/lib/libGL.so.1.2

/usr/lib/xorg/modules/*
(I really have no idea which files are important, so this is what i did!)

STEP 3:
   Now boot with your nVidia and install the driver downloaded from Nvidia website

I've downloaded 1.0-9755

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`

copy back the file
/usr/lib/xorg/modules/extensions/libglx.so
/usr/lib/libGL.so.1.2

from your temp folder, in "/usr/lib/xorg/modules/extensions/" libglx.so should be symbolic link!
RENAME the file you've copied in temp folder:
         libglx.so  ====> libglx.so.intel


STEP 4:
copy the rest of file back

that you've copied from "/usr/lib/xorg/modules/*"
BUT DO NOT OVERWRITE JUST SKIP IF THERE IS ANY CONFLICTS!!

now you are pretty much done

add few lines to the "stamina and speed script" to make it like following:


# sony_SZ series
VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then

ln -sf /etc/X11/xorg.conf.speed /etc/X11/xorg.conf
ln -sf /usr/lib/xorg/modules/extensions/libglx.so.1.0.9755 /usr/lib/xorg/modules/extensions/libglx.so
ln -sf /usr/lib/libGL.so.1.0.9755 /usr/lib/libGL.so.1

else

ln -sf /etc/X11/xorg.conf.1screen /etc/X11/xorg.conf
ln -sf /usr/lib/xorg/modules/extensions/libglx.so.intel /usr/lib/xorg/modules/extensions/libglx.so
ln -sf /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
fi




PS- right now i'm testing both modes with compiz and works fine so far....
I know i'm really bad at explaining but I hope this could help people with SZ

PS2 - If somebody has better way to deal with this or have problems please reply :) thx

---

### Post by hihihi on 2007-11-11
thank you so much!

this helped me as the link above.
i had to make the script for my system and now it is WORKING.
great,,,i am very happy now.
i dont have to copy xorgs before restarting on other graphic-card.
AND MOST COOL: OPENGL WORKS ON BOTH CARDS!!
thaNks again,,,,

btw:

i dont have a sony, its another laptop (alienware / uniwill / jewel) with an intel915g and nvidia go6600
AND i installed FIRST nvidia full enabled and afterwards i did this here: 

:lolflag:

here is how i did it (beware that most paths in the script bellow are adapted to my own enviroment, find them and replace them [like libglx]):

-- write a boot-script // graphic-card recognition on boot-up // :

1.) first of all i wrote two xorg.conf files:
one for nvidia, i called it xnvidia
one for intel, i called it xintel
and saved them in my home directory (/home/jo/)

2.) than i created an "intel"-folder under  /usr/lib/xorg/modules/extensions/
sudo mkdir  /usr/lib/xorg/modules/extensions/intel

3.) than i copied the exixting libglx.so in  /usr/lib/xorg/modules/extensions/ to  /usr/lib/xorg/modules/extensions/intel and renamed it to libglx.so.intel
sudo cp  /usr/lib/xorg/modules/extensions/libglx.so  /usr/lib/xorg/modules/extensions/intel/
sudo mv  /usr/lib/xorg/modules/extensions/intel/libglx.so /usr/lib/xorg/modules/extensions/intel/libglx.so.intel

4.) now we need the missing libgl.so.1.2
go to this site: [http://packages.ubuntu.com/feisty/libs/libgl1-mesa-dri](http://packages.ubuntu.com/feisty/libs/libgl1-mesa-dri) and download the package (not with the package-manager, just download it to your home directory)

5.) afterwards go to your /home/wherever/libgl1-mesa-glx_6.5.2-3ubuntu7_i386.deb and RIGHT-CLICK with the mouse, open with archive-manager:
you will see two tar.gz files: dubble-click on the data.tar.gz, dubble-click on the /. folder, dubble-click on the /usr folder and extract the libgl.so.1.2 file to your /home/wherever directory

6.) now copy  this libgl.so.1.2 to the intel folder in /usr/lib/xorg/modules/extensions
sudo cp /home/wherever/libgl.so.1.2 /usr/lib/xorg/modules/extensions/intel


7.) lets write the boot script to auto recognize the graphic-card

 sudo gedit /etc/init.d/vaio  (paste the text below)

#!/bin/bash

##switch between stamina and speed mode

VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then

cp -f /home/jo/xnvidia /etc/X11/xorg.conf

ln -sf /usr/lib/xorg/modules/libglx.so.1.0.9639 /usr/lib/xorg/modules/libglx.so

ln -sf /usr/lib/libGL.so.1.0.9639 /usr/lib/libGL.so.1

else

cp -f /home/jo/xintel /etc/X11/xorg.conf

ln -sf /usr/lib/xorg/modules/extensions/intel/libglx.so.intel /usr/lib/xorg/modules/libglx.so

ln -sf /usr/lib/xorg/modules/extensions/intel/libGL.so.1.2 /usr/lib/libGL.so.1

fi


8.)	sudo chmod 755 /etc/init.d/vaio
9.)	sudo ln -s /etc/inid.d/vaio /etc/rc2.d/S12vaio

THATS IT, REBOOT, BE HAPPY,
HAVE FUN, 
THANKS TO SHELTERED

---

