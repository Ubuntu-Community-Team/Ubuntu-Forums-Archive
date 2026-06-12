---
title: "/dev/human/brain/ sh HP TX1000 touch screen -easy!"
date: 2008-10-02
forum: Hardware
---

### Post by Bikergeek12533 on 2008-10-02
My HP tx1000 is working beautifully including the touch screen

Here is what i did,  

I visited [www.eeti.com.tw](www.eeti.com.tw) and went to the support page to download the
Linux driver

selected linux
and my appropriate kernel  and xorg
to find out go to a command line 
get into root by typing su

type  uname -a     
you will get the kernal version

thenitt
type X -version
you will get the version #

download matching package
for your 32 or 64 bit os

extract the gz archive somewhere in your home folder remember this (you will need it)

root@test-desktop:~# sh setup.sh
    (*) Linux driver installer for TouchKit controller

    (I) Begin to setup TouchKit driver.
    (I) Checking user permission: root, you are the supervisor.
    (I) Extract TouchKit driver package to /usr/local/TouchKit_x14.
    (I) Create TouchKit utility shortcut in /usr/bin.
    (I) Copy X module egalax_drv.so to /usr/lib/xorg/modules/input.

    (Q) Which interface controller do you use?
    (I) [1] RS232 [2] PS/2 [3] USB: 3
    (I) Using interface: USB
    (I) Found a HID compliant touch controller.
    (I) Found kernel module usbtouchscreen.
    (I) It is highly recommended that add it into blacklist.
    (Q) Do you want to add it into blacklist? (y/n) y
    (I) Add kernel module usbtouchscreen into
        /etc/modprobe.d/blacklist.
y (enter)

next you will need to re-boot then calibrate your screen

locate the calibration utility  you can run it directly from the archive.

follow instructions. 

the last thing you need to do is insert the line [Option "CorePointer"] to the egalax device section (without the brackets of course) and restart

enjoy your touchscreen 

R

---

### Post by romerotek on 2008-11-09
at first thanks for this col stuf.. i installed the usb driver successfully n is nw working... m using tx1218au.. with ubuntu 8.04... i also calibrated it.. 
  the system worked wel aftr the installaton, i can also use the touchscreen, but when ever i uses mouse aftr using the touchscreen everything except the mousepointer hangsup... i mean i can move the pointer but cannot select any thing on the screen.. same vth the case of touchscreen..
   also my usb doesnot recognises pendrives.. usb mouse connected is working... but pendrive or external harddisks are not working...:(

---

### Post by chunkypies on 2011-08-24
Hi there,

Did you manage to get the sound and the webcam to work? I have the tx1270ea and i cant seem to get these 3 things to work. any help would be great...oh and im using 11.04

ps. im a noob with linux

thanks

---

