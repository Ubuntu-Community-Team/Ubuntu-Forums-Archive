---
title: "Asus G1s laptop"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by srsEpix on 2007-06-14
Hi,

I'm interested in buying the Asus G1s laptop and I was wonder it anyone has this laptop and has installed Ubuntu on it.  If so, what works and what doesn't.  I'm especially interested in knowing if the wireless and bluetooth works.  

Thanks

---

### Post by ClockworkAvian on 2007-09-22
I'm running Gutsy Tribe 5 on it currently.  I had it install beautifully, without any of the SATA issues of installing Feisty.

Working out of the box:
[LIST]
[*]bluetooth
[*]wifi
[*]multimedia keys on the bottom
[*]nv driver at proper resolution.
[*]SD Card reader
[*]Wired ethernet

[/LIST]

Not tested by me:
[LIST]
[*]CF/XD/MMS readers
[*] any video out
[*]CD/dvd/lightscribe burning (reading works great)
[*]ESATA port
[/LIST]

Not working out of the box:
[LIST]
[*]flashy lights
[*]the display above the keyboard only says "Asus"
[*]sound is currently down. I don't recall if it DID work at one point, because i never actually checked, and i may have broken it (i've done that on my other system.)
[*]webcam
[/LIST]

This isn't comprehensive, and the stuff that doesn't work might be easily fixed by someone who knows what they're doing. I'm planning on writing a step by step guide to getting everything running flawlessly on this, but i'm new to linux, so it may take some time. when it's done though, i'll make a post of it.

---

### Post by Krischi on 2007-09-26
The webcam does work. There are just very few programs that support v4l2 at the moment. The luvcview program from the uvcvideo project works fine, and according to reports, the svn version of kopete also may support it. OpenWengo also is adding support for v4l2 in the next release.

Other features tested by me, which work fine:

[LIST]
[*]CD writing
[*]eSATA
[*]Sound
[/LIST]

The only thing that I have not been able to get to work as of now is the boot splash screen. I have to boot with splash set to off. If it works for you, could you please show me the contents of your /etc/usplash.conf file?

---

### Post by ClockworkAvian on 2007-09-30
I failed to mention, I'm running Kubuntu, not Ubuntu. So, there may be a difference in the splash system. Nonetheless, I've had no problems, and my /etc/usplash.conf is this:
```

# Usplash configuration file
xres=1024
yres=768
```


Thanks for the tip on the webcam! I got it working now. Here's a quick and dirty shell script that should get it up and going on any other systems.
install-webcam.sh
```

#!/bin/bash
# this script should get a Asus G1S webcam working. May also work on similar
# webcams, but i make no promises.
# As always, YMMV and use at your own risk.

#this installs the linux-uvc driver
cd /tmp
sudo apt-get install libsvn1
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
cd trunk
make && sudo make install


#This part installs luvcview
#downloads the latest version from here: http://mxhaard.free.fr/spca50x/Investigation/uvc/
wget http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz
gunzip -c luvc*.gz|tar -xf -
cd luvc*
make &&sudo make install


#Create a .desktop files
mkdir ~/Desktop/webcam-pictures
echo "
[Desktop Entry]
Encoding=UTF-8
Exec=luvcview -f yuv -w
Icon=camera
Name=Webcam Viewer
Path=~/Desktop/webcam-pictures
StartupNotify=true
Terminal=false
Type=Application
">~/Desktop/Webcam.desktop


```

execute that shell with 
```

sudo sh ./install-webcam.sh

```

---

### Post by Krischi on 2007-10-01
FYI: linux-uvc is part of the gutsy kernel, so it is not strictly necessary to install it from the svn repository, unless you want to make sure that you have the very latest version.

Thanks for the tip with the splash screen. I will try it out.

---

### Post by 9a3eedi on 2007-10-01
I installed Fiesty 32bit on my Asus G1S. Some of the stuff mentioned here didn't really work properly:

- X11. I think I need to update the opensource nvidia drivers. But in order to make it work, you can use VESA.. (for now)
- Wireless. The Asus uses the new Intel 4965 wireless chipset which supports the new 802.11n . I don't think Ubuntu Fiesty comes bundled with those drivers. I'm guessing Gutsy does though

also, booting from the LiveCD requires special instructions, like adding a boot time parameter called "break=top" then typing (without being able to look at the screen, because it's blank) 
'modprobe piix'
'exit'
and then it boots properly.

Otherwise, everything is working fine. I havent tested a lot of stuff though, like the webcam, sdcard, eSATA, CD/DVD-writing, etc.

As for the blinking lights and the small display, the drivers are windows only, and I can't seem to wine them either >_> .. there's a project in launchpad I think that is aiming to reverse engineer this and provide drivers for linux. Though nothing is really happening there. I'd go there if I had programming experience :P

Though imagine the possibilities if there was a linux driver for that. The ones in windows are quite... limited

---

### Post by rockclimber88 on 2007-10-01
I have Gentoo installed on my G1S-A1 (which is essentially the same thing as a G1S but with an A1 added to the end of the name.

I don't know how much of this is included in debian (and therefore ubuntu's) package manager but there is an nvidia driver for the graphics card, just search google for it and everything on the computer works except all the flashy bells and whistles like the little OLED screen that just says ASUS and the blinky lights and stuff.

I haven't even bothered to try the webcam drivers because I don't know what programs I would possibly be using that it would be useful for.

Also, if you have more than 2GB of RAM, and even if you don't actually, you should install the 64 bit version of your OS just because you can. I highly recommend it.
Also, make sure your kernel is > 2.6.19 to fix problems with ALSA

Links:
[http://wiki.archlinux.org/index.php/Touchpad_Synaptics](http://wiki.archlinux.org/index.php/Touchpad_Synaptics) -- touchpad driver
[http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi) --wireless drivers (if you're having problems with your wireless card)

You might also find this page useful even though it's for the ASUS G1 and not G1S:
[http://gentoo-wiki.com/HARDWARE_Asus_G1](http://gentoo-wiki.com/HARDWARE_Asus_G1)

---

### Post by UncleZeiv on 2007-10-07
Just found this preliminary driver for the oled display:

[http://lapsus.berlios.de/asus_oled.html](http://lapsus.berlios.de/asus_oled.html)

seems nice!

---

### Post by uqbar on 2007-11-29
Wht about the framebuffer console?
Mine is a G1S that has a 1440x900 display, but at the best I can only get an 80x25 console (that is boot diagnostics) by disabling the splash logo.
If I keep it enabled I get a blank screen until X starts.
Well, I run KUbuntu Gutsy.

---

### Post by uqbar on 2007-11-29
For the framebuffer console and the related boot splash, please see here:

[http://ubuntuforums.org/showthread.php?t=622018](http://ubuntuforums.org/showthread.php?t=622018)

---

### Post by jaz013 on 2007-12-05
I've just taken the plunge and loaded Kubuntu Gutsy 7.10 on my Asus G1S this week.  I have to say, everything went pretty damn well.

What works out of the box:
[LIST]
[*]USB
[*]Lan
[*]Wireless
[*]Card Reader
[*]Bluetooth
[*]Webcam
[*]Audio
[/LIST]

What works with some tweaking:
[LIST]
[*]Boot splash sceen (as per the above instructions)
[*]NVIDIA 8600GT running KDE and all the eyekandy (requires driver from nvidia.com)
[*]OLED display
[*]Wireless radio deactive notification (using ACPI and kNotify)
[*]Wine (for running Steam and HL2/TF2)
[*]Email LED (the blue one)
[/LIST]

What doesn't work:
[LIST]
[*]WLan flashy light
[/LIST]

I'm planning on writing my own OLED program that talks to the asus_oled kernel driver mentioned above.  Hopefully I'll get the thing to display some useful info (Clock, CPU, RAM, etc).  

To get the email LED working I'm using Mozilla Thunderbird for email and I have the **Thunderled** add-on installed.

The only thing I'm still having problems with is the webcam.  It DOES work out of the box, but I can't find any software that works with V4L.  The only app I have used (and the reason I know it works) is Kopete.  Which is great for video conferencing, but not for capturing the odd photo.

All in all, I'm pretty happy with how it's gone. :)

---

### Post by uqbar on 2007-12-06
1. Bluetooth is not working properly as there is a stupid bug in the distribution package. You cannot send files to the laptop through the BT connection. The fix has been found but never published! See [https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/146145](https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/146145)

2. S-ATA is not working at full steam as there's no way to enable the 32-bit mode and the DMA. Another annoying old bug with a known yet unreleased fix. See [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96693](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96693)

Maybe Ubuntu is not ready for prime time, unless you can wait some more months!

---

### Post by Warpnow on 2007-12-06
No flashylight is definitely a product killer. :D

---

### Post by jaz013 on 2007-12-08
> **Warpnow said:**
> No flashylight is definitely a product killer. :D

Damn straight!  How else will I know when someone is trying to ha><0r my matrix!?  :)

---

### Post by Miyabina on 2007-12-08
My SD card reader works but not my xD
Not sure how I would start diagnosing that.
Since my digi cam is xD and not SD :3

---

### Post by masternave on 2007-12-11
I'm going to try again... or I might wait till Hardy Heron. I dunno. I'm in a bit of a rut OS wise. Vista sux, don't want to buy another copy of XP, ubuntu doesn't let me play my games. I wanna dual boot, but last time I really screwed it up.

---

### Post by HoMie_G on 2007-12-15
I installed the shell script on my ASUS G1S, however when i want to load the camera i get an error stating: "Details: Failed to execute child process "luvcview" (No such file or directory)". 

iwhat could i have done wrong i just ran the script :S

Thanks

---

### Post by adam_r on 2008-01-30
what webcam does the G1S has? not syntek1255?

---

### Post by uqbar on 2008-01-30
My system reports it as

Bus 001 Device 002: ID 04f2:b012 Chicony Electronics Co., Ltd

Try with lsusb tool.

---

### Post by HoMie_G on 2008-02-03
I got the webcam working. I'm also writing a "how to" for the asus g1s. Help writing and updating it is appreciated.

here is the link:

[http://ubuntuforums.org/showthread.php?p=4261830#post4261830](http://ubuntuforums.org/showthread.php?p=4261830#post4261830)

Thanks,
HoMie_G

---

