---
title: "Help with usb tv card"
date: 2004-11-06
forum: Hardware &amp; Laptops
---

### Post by neon on 2004-11-06
Hi all,
         I've been trying to configure my hauppauge wintv usb card in linux for months (in mandrake, mepis and now in ubuntu) with no success.
I've tried with the usbvision driver but I get errors when I try to install it.

Can someone help me?

---

### Post by manontheroot on 2005-08-02
Hello
I use the hoary and i finally success in the installation of a wintv usb 1.0 :

First of all, you need to download the usbvision driver from : [http://usbvision.sourceforge.net](http://usbvision.sourceforge.net)

then you need to compile it (verify that you have the kernel header and the tree) and to install it (it is the difficult part ;-)

then you type :
modprobe usbvision

insert your wintv, and verify that it is recognized by the driver with :
dmesg

install xawtv and zapping with synaptics

for using xawtv, type :
xawtv -noxv -capture grabdisplay

here is my xawtv config file (~/.xawtv), I am in France :
----------- Début de la copie -------------------------
[global]
ratio = 4:3
freqtab = france
# pixsize = 128 x 96
pixsize = 128 x 96
pixcols = 1
jpeg-quality = 75
keypad-ntsc = no
keypad-partial = yes
osd = yes
osd-position = 30 , 20
use-wm-fullscreen = yes

# [Station name]
# capture = overlay | grabdisplay | on | off
# input = Television | Composite1 | S-Video | ...
# norm = PAL | NTSC | SECAM | ...
# channel = #
# fine = # (-128..+127)
# key = keysym | modifier+keysym
# color = #
# bright = #
# hue = #
# contrast = #

[defaults]
group = main
norm = SECAM
input = Television
capture = grab
color = 49%
bright = 49%
hue = 49%
contrast = 74%

[TF1]
channel = 25

[France2]
channel = 22

[France3]
channel = 28

[Canal+]
channel = 6

[France5]
channel = 30

[M6]
channel = 33
----------- Fin de la copie -------------------------

the best image I obtained is with zapping.

Hope it will work for you  ;-)

---

### Post by alpianon on 2006-03-17
Ubuntu 5.10 - driver usbvision 0.9.8.2 for Hauppage WinTV USB

1- Go to [http://usbvision.sourceforge.net/](http://usbvision.sourceforge.net/) and dowload the sources
(version 0.9.8.3 can't be compiled under Ubuntu 5.10, you have to download v0.9.8.2)

Here's the direct link for lazy people
[http://prdownloads.sourceforge.net/usbvision/usbvision-0.9.8.2.tar.gz?download](http://prdownloads.sourceforge.net/usbvision/usbvision-0.9.8.2.tar.gz?download)


2- Save it in your home directory


3- In Synaptic, enable the Universe repository


4- You need to install make, gcc-3.4, linux-headers; you need also "zapping" to watch tv (it is far better than xawtv!)
You have to complile and install the module, then you may add a script to load it during startup

Open a console window, then type:
(please note that the character ` is not ' and it can be obtained with AltGr+' - anyway, you may just copy and paste the following lines)

sudo apt-get install make gcc-3.4 linux-headers-`uname -r` zapping
tar -xf usbvision-0.9.8.2.tar.gz
cd usbvision-0.9.8.2/src
sudo make
sudo make install
sudo modprobe usbvision
echo -e "modprobe usbvision\n" >usbvision
sudo cp usbvision /etc/init.d
cd /etc/init.d
sudo chmod 755 usbvision
sudo update-rc.d usbvision start 51 S .

( . at the end of the line is needed!)

4- Connect the WinTV USB card, and run zapping (it should be in the Audio&Video menu)

Cheers!
Alberto Pianon (Italy)

---

### Post by visarya on 2006-11-09
vishal@vishal-desktop:~/Desktop$ tar -xf usbvision-0.9.8.2.tar.gz
vishal@vishal-desktop:~/Desktop$ cd usbvision-0.9.8.2/src
vishal@vishal-desktop:~/Desktop/usbvision-0.9.8.2/src$ sudo make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/vishal/Desktop/usbvision-0.9.8.2/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/vishal/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.o
/home/vishal/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:40: error: expected ‘)’ before string constant
/home/vishal/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:208: error: unknown field ‘name’ specified in initializer
/home/vishal/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:208: warning: initialization from incompatible pointer type
/home/vishal/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:209: error: unknown field ‘id’ specified in initializer
/home/vishal/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:209: error: ‘I2C_ALGO_BIT’ undeclared here (not in a function)
/home/vishal/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c: In function ‘i2c_usb_add_bus’:
/home/vishal/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.c:226: error: ‘struct i2c_algorithm’ has no member named ‘id’
make[2]: *** [/home/vishal/Desktop/usbvision-0.9.8.2/src/i2c-algo-usb.o] Error 1
make[1]: *** [_module_/home/vishal/Desktop/usbvision-0.9.8.2/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [default] Error 2
vishal@vishal-desktop:~/Desktop/usbvision-0.9.8.2/src$ 




i already tried 0.9.8.3 also , from tar and cvs thats also dont work
any suggestions

---

### Post by visarya on 2006-11-11
#ok here how i fixed its 
#i was missing build-essential linux-kernel-headers
sudo apt-get install linux-kernel-headers
sudo apt-get install build-essential

#got the src from  cvs
cvs -z3 -d:pserver:anonymous@usbvision.cvs.sourceforge.net:/cvsroot/usbvision co -P usbvision
cd usbvision/src
sudo make
sudo make install
sudo modprobe usbvision
echo -e "modprobe usbvision\n" >usbvision
sudo cp usbvision /etc/init.d
cd /etc/init.d/
sudo chmod 755 usbvision
sudo update-rc.d usbvision start 51 S .

---

### Post by edog on 2006-11-25
hey thanks for the help from this post but now when i plug in my wintv usb i get the folling 
[17179589.788000] /home/edog/usbvision/src/usbvision.c: USBVision[0]: registered USBVision Video device /dev/video0 [v4l]
[17179589.788000] /home/edog/usbvision/src/usbvision.c: USBVision[0]: registered USBVision VBI device /dev/vbi0 [v4l] (Not Working Yet!)

from this when i run say zapping the app can not get info from the usb and such no tv .

Thanks in advace for any help

btw im useing kernal 2.6.15-27-386

---

