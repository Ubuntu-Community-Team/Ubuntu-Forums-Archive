---
title: "Archos 9 and Poulsbo (GMA 500)"
date: 2010-01-14
forum: Hardware
---

### Post by chrismcb6 on 2010-01-14
Hi,
 
I posted in the Multimedia & Video forum last week with this problem - but it was perhaps the wrong place.
 
[http://ubuntuforums.org/showthread.php?t=1372522](http://ubuntuforums.org/showthread.php?t=1372522)
 
My problem is getting the Poulsbo drivers to work with the new Archos 9 tablet.
 
Everything is installed and I've followed the Ubuntu Wiki instructions to set up the driver, but there seems to be more going on with this device.
 
I've attached the X logs (same as on the other board) and xorg.conf in the hope that someone can shed some light onto what the device is doing?
 
 
Everything else (wifi, bt, software) is working fine (Except the touch screen drivers which I've not bothered to tackle yet) - it's just the poor performance with the VESA defaults making it unusable.
 
Currently running Ubuntu Netbook Remix 9.10 with kernel 2.6.31-17-generic and all updates installed.
 
 
 
Thanks

---

### Post by chrismcb6 on 2010-01-15
A shameless bump here - hoping that someone could pick up the thread?

---

### Post by pabloda on 2010-05-02
Have you tried with the new 10.04?
EDIT: Or maybe Jolicloud, since it has GMA500 driver built in.

---

### Post by chrismcb6 on 2010-05-03
Thanks - I did try the Jolicloud "PreBeta", but I will download Ubuntu 10.04 and the new Jolicloud "PreFinal"

---

### Post by pabloda on 2010-05-03
Nice, tell me how it went :D

---

### Post by ledzepjes on 2010-06-10
Hi guys, I found this while reading your thread, have you come up with anything, I'm assuming you haven't yet. Try this, these guys claim to have the touch screen working, as well as wireless, let me know if it works, it looks like a nice little touch screen pc to have ubuntu on:

[http://gadgetmix.com/index/archos9-ubuntu/](http://gadgetmix.com/index/archos9-ubuntu/)

Copied from the site above:

Archos 9 is a an x86 computer and thus it is possible to install Ubuntu on it. Folks at archoslounge installed it on the Archos 9, but the installation is not so straightforward. You will need to attach a USB mouse, keyboard, Wi-Fi dongle to the Archos as touchscreen and built-in Wireless do not work out-of-the box.

After installing the Ubuntu, to get the wireless working, write the following commands in the terminal:

[COLOR="DarkOrange"]sudo apt-add-repository ACH: gma500/ppa

sudo apt-get update

sudo apt-get install Poulsbo-driver-2d-3d-driver Poulsbo Poulsbo-config[/COLOR]

..and to get the touchscreen working, write this at the terminal

[COLOR="DarkOrange"]wget [http://home.eeti.com.tw/web20/drivers/touch_driver/Linux/20100413/eGalaxTouch-3.01.4001-32b-k26.tar.gz](http://home.eeti.com.tw/web20/drivers/touch_driver/Linux/20100413/eGalaxTouch-3.01.4001-32b-k26.tar.gz) 
tar vxfz eGalaxTouch-3.01.4001-32b-k26.tar.gz vxfz eGalaxTouch tar-3.01.4001-32b-k26.tar.gz 
cd eGalaxTouch32 cd eGalaxTouch32 
sudo ./setup.sh sudo. / setup.sh 
choose PS/2 by pressing "2" choose PS / 2 by pressing "2"[/COLOR]

Change the startup options to enable the touchscreen to be recognized (this causes the loss of the mouse touchpad).

[COLOR="DarkOrange"]sudo gedit /etc/default/grub sudo gedit / etc / default / grub[/COLOR]

It should be added mem = 980mb i8042.nomux content GRUB_CMDLINE_LINUX_DEFAULT line and save.

[COLOR="DarkOrange"]sudo update-grub sudo update-grub[/COLOR]

3. Make the screen visible to the system

[COLOR="DarkOrange"]sudo vim.tiny /etc/rc.local vim.tiny sudo / etc / rc.local[/COLOR]

It should be added [COLOR="DarkOrange"]echo-n "serio_raw"> / sys/bus/serio/devices/serio1/drvctl[/COLOR] just before the exit 0.

4. Restart and calibrate the screen

[COLOR="DarkOrange"]sudo eGalaxTouch sudo eGalaxTouch[/COLOR]

Adjust the compensation by selecting Tool> Linearization> 25 points and clicking at each round that appear on the screen.

---

### Post by tonymaro on 2010-06-21
Actually the English translation you took that from is missing a step - the Poulsbo drivers are for video, not wireless.

To get the wireless working you need to install broadcom-sta from the restricted repositories.

---

### Post by tonymaro on 2010-06-27
Here's a better tutorial I wrote (in English,) without the need for an external wireless gadget, too:

[http://www.ossramblings.com/installing-ubuntu-archos-9-tablet](http://www.ossramblings.com/installing-ubuntu-archos-9-tablet)

---

### Post by pabloda on 2010-07-04
aparently now jolicloud has touchscreen support.

---

