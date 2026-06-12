---
title: "Stuck TX1120us HP Tablet"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by petroz on 2007-05-14
Hi All,

I have a new tx1120us hp tablet. I dont want to overload this post with specs, so you can find them at 
[http://h10025.www1.hp.com/ewfrf/wc/g...reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/g...reg_R1002_USEN)
I have not been able to get any Ubuntu distrib to succesfully startx from any installation image. The screen goes through the color spectum to a strait black. I have also tried a few other os's like slax, solaris, gentoo and suse. So far the only success I have had was with suse and a live demo cd of looking glass on slax with the newest display drivers for my grapics card. I think that I am having a problem the display driver. I really want to use only Ubuntu. If there is any help or advice anyone can give me it would be greatly appreciated.

---

### Post by Mikecore on 2007-05-14
You need to configure your xorg.conf by hand to make this work.  I think there is a section in the xorg.conf file that needs to be un commented for tablet PCs next I think if your running the nvidia driver you need to disable the starup nivida logo. And last I think there is another options setting that needs to be added to your driver section of the xorg.conf to get the Xserver running. I can't exactly remmeber what I had to do. but if you google "nivida black screen linux " you will find the answer.

Good Luck

---

### Post by diatribex on 2007-05-14
Err..I dont know about all that...The latest ubuntu worked right out of the box for me on my tx1120 using the 32bit alternate install cd.  Once installed i switched to the restricted drivers for full 3D.  Do a couple searches around this site for tx1000 and/or tx1120, as there are few who have this working. You should not have to go futzing around with the xconf ( at least not until you want the touch screen working)

Jordan

---

### Post by farbird on 2007-05-15
to get into the login screen [ gui ]
try this

click escape before it boots..

edit the line which have the "uuid=xxxxxx" text..

append to the same line with these codes " noapic vga=0x317"
it should get it up to the gfx login screen.


once u get in...
nano edit your /boot/grub/menu.lst file and make the line permanent..

> **petroz said:**
> Hi All,

I have a new tx1120us hp tablet. I dont want to overload this post with specs, so you can find them at 
[http://h10025.www1.hp.com/ewfrf/wc/g...reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/g...reg_R1002_USEN)
I have not been able to get any Ubuntu distrib to succesfully startx from any installation image. The screen goes through the color spectum to a strait black. I have also tried a few other os's like slax, solaris, gentoo and suse. So far the only success I have had was with suse and a live demo cd of looking glass on slax with the newest display drivers for my grapics card. I think that I am having a problem the display driver. I really want to use only Ubuntu. If there is any help or advice anyone can give me it would be greatly appreciated.

---

### Post by farbird on 2007-05-15
to get your wifi broadcom working, try this

sudo apt-get install bcm43xx*

sudo gedit /etc/iftab

change the interface name of the wifi interface to "wlan0"
it may be eth0 or eth1 initially [ check to ensure which is the wifi one ]

sudo gedit /etc/network/interfaces
remove all lines which make references to the old "ethx" that has been replaced above to "wlan0"

now in console, do this

sudo rmmod bcm43xx
sudo modprobe bcm43xx

this should get it working...
if the rmmod doesnt work, just reboot the laptop....

if still cannot work... post reply here

---

