---
title: "nVidia 190 driver seems to cure &quot;screen flash&quot; problems"
date: 2009-11-18
forum: Hardware
---

### Post by Land Rover Series 3 on 2009-11-18
Hi,

I'm new to Ubuntu and Linux (just a couple of days experience), so please forgive if this post states the obvious to those of you who have more know-how about these things than I do.

I've been trying to install an nVidia driver for my GeForce Go 7600 that doesn't keep giving me continuous "screen flashes" every so often. Have tried just about every driver suggested, but all had the same problem. I think I may have finally cured it, so am posting this in case it might help others faced with the same problem...

nVidia GeForce Go 7600

Used the Ubuntu Hardware Drivers utility to remove any existing nVidia drivers
Rebooted
Downloaded "NVIDIA-Linux-x86-190.42-pkg1.run" onto my Desktop from the link via the Debian web site
Entered (Ctrl-Alt-F1) to get a terminal screen
Logged in using my normal name and password
Typed "cd Desktop" to change directory to my Desktop
Typed "sudo /etc/init.d/gdm stop" to turn off the Gnome Display Manager (and ignored the suggestions)
Typed "sudo sh NVIDIA-Linux-x86-190.42-pkg1.run" to run the installer
   (it automatically built the kernel etc.)
   (Chose the automatic configuration option)
Typed "sudo reboot" to reboot the computer
System rebooted, lots of messages that I don't understand...
BUT...

So far (touch wood) system looks great, seems rock solid, and not a single "nVidia screen flash" has happened!!

Hope that might help someone

---

### Post by anupsg on 2009-12-01
but it asks stop xserver ......... and i dint get how to install plugins....... when i try to play *.mp3 files .... its not takin automatic download from net.....?

---

### Post by Land Rover Series 3 on 2009-12-01
> **anupsg said:**
> but it asks stop xserver ......... and i dint get how to install plugins....... when i try to play *.mp3 files .... its not takin automatic download from net.....?
I'm not following what your thread is trying to say. What has installing nVidia drivers got to do with playing music files?????

You have to download the driver to your Desktop before you start this operation.
Rebooting will re-start the desktop automatically.

---

### Post by Leomega on 2010-02-17
Hi.

I was having problems with my NVIDIA drivers in ubuntu 9.1, as I could not choose any screen resolution above 1024x762.
So, I tried follow your guide and installed the latest NVIDIA Linux drivers (190.53) and it installed perfectly. But now after the update, I am only able to run in 640x480 resolution! What the hell??
I am using gforce 7900 and downloaded the correct drivers.

Can you or anyone else tell me what I am doing wrong? I have tried googling for an answer or similar problems for 2 days without any progress.

Best regards

---

### Post by boot_sectorz on 2010-02-17
Hi,
Try installing the latest drivers (195) and see how it goes. Check the simple install guide on: 
[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

U can simply install after 'update source list' by going to >System > Administration > Hardware Drivers... Choose version 195.

Good luck

---

### Post by Vinnare on 2010-02-18
I've installed Ubuntu only yesterday in my new laptop everything worked out fine till I installed the nVidia display driver suggested by its search. When I rebooted, the display went blank after displaying the normal ubuntu startup circles. Actually the display gets switched off and NOT BLACK (you can mke that difference easily) but the system keeps on. You can infact even log in if you type the password (as if blindfolded, of course ), you know this by the welcome music. Then you can do the work too if you know how to use the keyboard.

When I tried starting in the recovery mode then I did as suggested in most of the other forums i.e. type the command:
sudo dpkg-reconfigure xserver-xorg
but unlike as suggested the rest of the process does not follow and the command line reappears.

Please suggest some solution. **My GPU is NVIDIA GT330M**.
I'm new to linux.

Thnx anyhow

---

