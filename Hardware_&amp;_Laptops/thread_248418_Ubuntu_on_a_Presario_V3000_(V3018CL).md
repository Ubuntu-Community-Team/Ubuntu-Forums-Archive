---
title: "Ubuntu on a Presario V3000 (V3018CL)"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by reedatschool on 2006-09-01
I recently purchased a Compaq Presario V3000 series computer.  After quickly getting fed up with the pre-installed Windows XP, I decided to see what a little Ubuntu 6.06.1 would bring to the plate.

Worked out of the Box:

Sound
Basic Graphics (No wide screen resolution)
Memory Card Reader
Lan Card 
DVD Drive
Lid close functionality
Volume Control hot keys
Touchpad Motions (At least the ones I use)


Worked with some TLC:

Accelerated graphics with proper wide screen resolution
Wirless Network Card (Broadcom 4311)

Additional Info:

To get hardware acceleration and proper resolution I just installed the commercial Nvidia drivers from the repo and set the only available resolution to 1280X800.  Upon restart everything worked perfectly.

To get the Wireless to work I used a freshly compiled version of the new ndiswrapper util at 

[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148)

I followed most of the walkthrough here 

[http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311](http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311)

After some tinkering I was able to get the wireless card to work, but the network manager included for gnome had issues with configuring card.  I had to setup Wlan0 in Networking and use the default network manager to get things working properly.  

I did have a go at the 64 bit version with the wireless drivers that where in the Windows partition and it worked like a charm.  Despite my success with the 64 bit version of Dapper I was dissapointed to find out there are still some 32 bit commonly used programs that have not been ported yet. 

Now I am running XGL with Compiz and my laptop is looking way nicer than any other OS on or soon to be on the market.  Great for showing off how Ubuntu really rocks the block around campus.

Reed Harding

---

### Post by Exclamation on 2006-09-01
I have the same wireless chip but cant seem to get it working under 64bit.
[http://www.ubuntuforums.org/showthread.php?t=246149](http://www.ubuntuforums.org/showthread.php?t=246149)

Maybe you could help.

---

### Post by twade on 2006-09-07
Could you post more details on how you installed the nvidia drivers?  I'm fairly new to linux and would really like to be able to get the display and wireless working well.  anything else is gravy.

Thanks

---

### Post by reedatschool on 2006-09-08
Nvidia drivers are pretty easy nowadays (I used to have to compile them!) Straight from the unofficial Dapper guide at

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

All you do is open a terminal and cut and paste 

sudo apt-get install nvidia-glx nvidia-kernel-common

then

sudo nvidia-glx-config enable

This works 99% of the time.. ocasionally you have to edit you /etc/X11/xorg.conf and change the instance of nv to nvidia

If you had a wide screen and were forward thinking enough to select the proper resolution to begin with, it should start working correctly on a restart.  

If not you can run 

sudo dpkg-reconfigure xserver-xorg

from a terminal to reconfigure you Xserver, just be sure to set the right resolutions this time.

---

### Post by frank_costanza on 2006-10-03
I also installed 64-bit Dapper on my V3000 but I have problems with lid close.  It worked when I installed 32-bit Dapper. Under 64-bit, the computer goes into suspend OK, but when I open the lid, the screen never turns on. The computer turns back on as I can see disk activity and all of the other lights are on.

Has anyone else had this problem?  Can someone who has this working post their xorg.conf and acpi-support files?

One other thing is that I installed the nvidia driver via Automatix...not sure if that makes a difference.

Thanks!

---

### Post by fooblah on 2006-10-30
There is now a wiki for V3000 series and other hp laptops at:

[http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A]("http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A")

We are trying to pool all the specific problems and solutions in one place so check it out and update with fixes as they are found.

thanks.

---

