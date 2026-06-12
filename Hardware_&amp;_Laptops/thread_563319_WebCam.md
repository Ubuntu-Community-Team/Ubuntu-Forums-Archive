---
title: "WebCam"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by saitoh on 2007-09-29
I have a Dell XPS M1210 with a OEM Logitech webcam/microphone. The Device ID is 046d:08c6 making this fall under the UVC drivers. So I downloaded the UVC driver, edited the Makefile to "INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo" and attempted to make install. The webcam still doesn't work, nor has it for edgy or feisty. I am currently running gutsy and this issue was brought to my attention again because when I upgraded to gutsy it erased my previous configuration which after weeks of messing around I was able to get Ubuntu to stop sending massive amounts of power to the camera which makes it really hot and kills my battery life.

Anyways my fstab looks like so:

proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=0d2e4fa4-551b-4d4c-aecc-cd75f8e0580c / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda1 :
UUID=07D7-0406 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda2 :
UUID=D62CB0C32CB0A043 /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda3 :
UUID=3f78cd3b-0692-4094-aeb7-e4653bc3f807 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

it has all of my hard drive partitions mounted, but I don't see my camera anywhere. Any help would be really appreciated.

update:
If i run "modprobe uvcvideo" I get nothing

---

### Post by saitoh on 2007-09-30
bump

---

### Post by saitoh on 2007-09-30
I was able to install the WebCam by doing the following:

1. To get the UVC driver type "svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk"
2. Now go the folder trunk by opening a terminal and typing"cd trunk"
3. You need to change the install path in the Makefile so type
     "sudo vi Makefile" and change 
     INSTALL_MOD_DIR := usb/media
     to
     INSTALL_MOD_DIR := kernel/ubuntu/media/usbvideo
4. Then you need to compile it so type "sudo make install". Your webcam driver is now installed, but you still need a program to use it and most
    are not compatible with the UVC drivers (easycam will not work 99% of the time).
5. So go here [http://mxhaard.free.fr/spca50x/Investigation/uvc/](http://mxhaard.free.fr/spca50x/Investigation/uvc/) and get the latest luvcview.tar.gz file.
6. You now need to extract the files so go to where you downloaded them to usually the desktop ("cd ~/Desktop/") and type "tar -xzf  luvcview(here you
    need to put the rest of the file name which changes depending on what version you are using.)".
7.You now need to install some lib files so open synaptic package manager and search for "SDL", you need to install a lib file named "libsdl1.2-dev" there  
   are several similar named libs that are installed in Ubuntu by default so make sure you click that one.
8. Now you need to go back to your terminal go do the folder that was created by step 6 and type "sudo make install" .
9. Your all done just type luvcview and a window will pop up with the video from your webcam.

I tried to make this as newb proof as possible I got all my information from:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) 
and UVC's wiki:
[http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC)

So if you have problems these places will give you answers.

---

### Post by mccurry on 2007-10-05
it works out of the box for ekiga, just fyi.

I have a m1210 as well. Let me know what works for you.

---

