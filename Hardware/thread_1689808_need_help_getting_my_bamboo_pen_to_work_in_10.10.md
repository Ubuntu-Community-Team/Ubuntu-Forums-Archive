---
title: "need help getting my bamboo pen to work in 10.10"
date: 2011-02-17
forum: Hardware
---

### Post by clear on 2011-02-17
sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get install wacom-dkms

thats what i used and it worked great, but from what i understand, the its a very old driver fix. and currently, theres no easy way for the latest drivers in 10.10. i saw that huge 'how to' list and was just curious if theres a easier way. i just dont understand what i need to do. im also using the ati propriatary drivers which i updated too after installing that terminal code. 

right now my pen is working great (ctl460)but i read that it will stop working when a new security update is released. what do i need to do to get my pen working with the best drivers? and should i avoid the proprietary drivers for any reason. help would be greatly appreciated:-k

:edit: reformatted and did this, cd ./Desktop

wget [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.8-10.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.8-10.tar.bz2)

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade

sudo apt-get install linux-headers-generic

tar xjvf linuxwacom-0.8.8-10.tar.bz2

cd linuxwacom-0.8.8-10

./configure --enable-wacom --prefix=/usr

sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

sudo depmod -a

(After rebooting if not working check if the wacom.ko is auto-loading with lsmod.)

lsmod | grep wacom

(you should see 'wacom' with some other stuff)

i don't see a control panel though. i want to disable the stylus buttons as they just get in the way.

---

### Post by Favux on 2011-02-17
Hi clear,

I don't think there is a way to disable the stylus buttons.  First time I've heard anyone request that "feature" anyway.  :)

The reason the compiled usb kernel driver/module wacom.ko stops working after a kernel update is that the new kernel creates a new modules directory that has the old default non-working wacom.ko.  So you have to recompile to get a working wacom.ko and copy it into place over the old non-working wacom.ko.

The X driver for wacom in Maverick comes from xf86-input-wacom not linuxwacom.  And xf86-input-wacom does not have wacomcpl (Wacom Control Panel) like linuxwacom did.  They dropped it.

---

### Post by clear on 2011-02-18
theres quite a few things im :confused: about

sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade

sudo apt-get install linux-headers-generic

tar xjvf linuxwacom-0.8.8-10.tar.bz2

cd linuxwacom-0.8.8-10

./configure --enable-wacom --prefix=/usr

sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

sudo depmod -a

(After rebooting if not working check if the wacom.ko is auto-loading with lsmod.)

lsmod | grep wacom

(you should see 'wacom' with some other stuff)

i do see wacom, the driver works. obviously bad idea to disable stylus buttons... did i install the right driver for my ctl460? i know theres two. xdriver, and x86. following those instructions which driver did i install? which driver should i have installed? what does recompile mean. is it hard? i just want to make sure i did it correctly.. i have an ati4850 card would i 'break' the drivers(whichever i installed) by updating to proprietary drivers that being fglrx?

---

### Post by Favux on 2011-02-18
Hi clear,

Although you didn't include the download lines the instructions you show indicate you compiled the wacom.ko.  Which is the usb kernel driver/module.  That was the correct driver to install.  And that is what you would need to do again if a kernel update breaks it.

Since you have a CTL460 or Bamboo Pen you do not need to worry about compiling the X driver, xf86-input-wacom.  The default, which is xf86-input-wacom-0.10.8, in Maverick will work fine for the stylus.

There should be no problem using "fglrx".

---

### Post by clear on 2011-02-18
> **Favux said:**
> Hi clear,

Although you didn't include the download lines the instructions you show indicate you compiled the wacom.ko.  Which is the usb kernel driver/module.  That was the correct driver to install.  And that is what you would need to do again if a kernel update breaks it.

Since you have a CTL460 or Bamboo Pen you do not need to worry about compiling the X driver, xf86-input-wacom.  The default, which is xf86-input-wacom-0.10.8, in Maverick will work fine for the stylus.

There should be no problem using "fglrx".

should i have included the download lines. what are they? would the driver work better, (you know make me 10 times more artistic) jk. bt would they work better if i added the dl lines?

---

### Post by Favux on 2011-02-18
You must have included the download lines in order to compile the wacom.ko.  So don't worry about it.  I just meant it would have been more obvious what you were compiling, had you included them.

The stylus or pen is working now, correct?

---

