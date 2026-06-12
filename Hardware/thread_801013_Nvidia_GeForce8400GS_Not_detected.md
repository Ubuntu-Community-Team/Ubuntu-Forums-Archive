---
title: "Nvidia GeForce8400GS Not detected"
date: 2008-05-20
forum: Hardware
---

### Post by Xfact0r82 on 2008-05-20
I had everything running fine and dandy in 7.10, I upgraded to 8.04 and now the only resolutions available are 800x600 and 640x480.  I have installed everything at least once if not twice(which may be the problem).  Not sure where to go from here, I can post anything that will help in solving the problem.  

Note: I am a new fairly recent convert to linux and I love it, but sometimes I don't quite understand how to use command/terminal.

Thank you for any and all help.

---

### Post by Lorathal on 2008-05-20
Since youre a beginer on linux i shall help you by explaining one of the comands u will need most:

sudo apt-get install [name of the program]

This conects you to the servers in search of the program and install it on your linux its quite a nice feature , for your case you can download the program ENVY, it will read your machines features and download/install the best driver for your graphic board and it will configure some stuff.

so if you want the program you will write:

sudo apt-get install envy

gl solving the problem :)

---

### Post by PmDematagoda on 2008-05-20
How did you install the Nvidia driver in 7.10? Was it manually or via Restricted Drivers Manager?

---

### Post by Xfact0r82 on 2008-05-20
IN 7.10 i believe I used Envy, and tweaked the xconf file , but i do not remember what i did.  I used the new envyNG on 8.04, after it does its thing and i reboot, when i try to go to nvidia x-server settings i get the following message
[COLOR="Red"]"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."[/COLOR]

I have tried to uninstall using envy only to leave my display almost unusable, it feels like something is not right with the conf file, but i really haven't a clue

---

### Post by Xfact0r82 on 2008-05-20
I have figured out that i can get to a default setup that gives me better resolutions by use recovery mode and picking the fix x-server option.

when this is done it turns off or uncecks the driver under hardware drivers, i still get the error above when i try to use nvidia-xserver.  
any and all help is appreciated

thank you so much in advance for sharing your wisdom

---

### Post by signseeker on 2008-05-20
Does nvidia-settings work?

---

### Post by Xfact0r82 on 2008-05-20
No when I go to system|admin|nvidia xserver settings i receive the message
[COLOR="Red"]"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."[/COLOR]

---

### Post by signseeker on 2008-05-20
> **Xfact0r82 said:**
> No when I go to system|admin|nvidia xserver settings i receive the message
[COLOR="Red"]"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."[/COLOR]

So try 'sudo nvidia-xconfig' in a terminal and see what happens?

---

### Post by Xfact0r82 on 2008-05-21
Ok i got it working using the restricted drivers, but i would prefer to use the nvidia(envyNG)drivers so that I can more easily configure my display ie: dual monitors.

When i would console nvidia-xconfig, it spit some error massage out at me, i will try to reproduce it, but as i do not currently have that installed it may be difficult to repeat.

---

### Post by signseeker on 2008-05-21
> **Xfact0r82 said:**
> Ok i got it working using the restricted drivers, but i would prefer to use the nvidia(envyNG)drivers so that I can more easily configure my display ie: dual monitors.

When i would console nvidia-xconfig, it spit some error massage out at me, i will try to reproduce it, but as i do not currently have that installed it may be difficult to repeat.

Using sudo nvidia-settings allowed me to set up dual monitors with about 4 mouse clicks. :)

---

### Post by puzzledinmn on 2008-05-21
I have an even weirder problem with my 8400GS.  When I selected the NVidia restricted driver to get high resolution I got booted back into an old level of 7.10 (which I noticed is still listed in GRUB).  If I do repeated reboots I can sometimes get back into 8.04 but haven't been able to get high resolution.  Looks like something is seriously wrong and I have no idea where the old 7.10 desktop came from.  I am just using the restricted drivers manager.

update- I got high resolution by manually configuring (at the boot configure resolution box) the open source NVidia driver and selecting 1440x900 for my Dell SE198WFP display @60Hz.  I guess I could be happy with that except I'm still booting back to 7.10 about a third of the time.  Any way to kill the 7.10 boots or is it time for a total reinstall?  Pretty scary upgrade.

another update- my problems were caused by grub booting to my clone drive and the update being installed there.  After I deleted the clone partition and redid the update on my primary drive, the update correctly applied the restricted Nvidia driver.  It looks like the update just copied the X11.conf file as my display is now supported but is not shown there correctly.

---

### Post by VayHow on 2008-05-21
I have a 8600M GT on my laptop, and it works fine. After my fresh install of Hardy, I updated the whole system from source, then restricted driver successfully enabled. Before I did that, the driver status was abnormal (displayed as "not in use" but with a check on the driver) So if possible, you can try a fresh install. I know this sounds a little clumsy, coz I'm newbie, too.

---

### Post by Victormd on 2008-05-21
> **puzzledinmn said:**
> I have an even weirder problem with my 8400GS.  When I selected the NVidia restricted driver to get high resolution I got booted back into an old level of 7.10 (which I noticed is still listed in GRUB).  If I do repeated reboots I can sometimes get back into 8.04 but haven't been able to get high resolution.  Looks like something is seriously wrong and I have no idea where the old 7.10 desktop came from.  I am just using the restricted drivers manager.

update- I got high resolution by manually configuring (at the boot configure resolution box) the open source NVidia driver and selecting 1440x900 for my Dell SE198WFP display @60Hz.  I guess I could be happy with that except I'm still booting back to 7.10 about a third of the time.  Any way to kill the 7.10 boots or is it time for a total reinstall?  Pretty scary upgrade.

you can edit grub and remove the 7.10 entries...
```
sudo gedit /boot/grub/menu.lst
```
but you'll still have 7.10 installed... I don't know enough to tell how to remove that without damaging your current install (I would probably try on mine, but nobody else's).
If editing menu.lst doesn't work, I would probably do a clean install. I had several issues when upgrading and struggled with them for quite a while... until I did a fresh install... and now everything is perfect!

---

### Post by Xfact0r82 on 2008-05-22
when I run sudo nvidia-xconfig i receive the following message.
[COLOR="Red"]Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first CorePointer in the config input list.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'[/COLOR]


So then i try again to do sudo nvidia-settings since that is what the above command supposedly fixed. and i am greeted once again with this message
[COLOR="Red"]You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.[/COLOR] 

[COLOR="Black"][/COLOR]I currently have unchecked the restricted drivers and it is in use.  My max resolution is 800x600 and i have run EnvyNG.  If anyone has the steps they took to get their card setup i would appreciate that.

Also what happened to the screens and graphics section under admin menu?

---

### Post by puzzledinmn on 2008-05-22
I found out I have two /boot/grub/menu.lst files and the one when I boot into 8.04 that one looks correct but I never see that one when I boot.  see post at

[http://ubuntuforums.org/showthread.php?t=802923](http://ubuntuforums.org/showthread.php?t=802923)

---

### Post by Xfact0r82 on 2008-05-27
Thank you all for your help and suggestions.  I decided to just do a fresh/clean install, and all is once again happy in my ubuntu world.  All drivers work as they should and I couldn't be happier.

---

