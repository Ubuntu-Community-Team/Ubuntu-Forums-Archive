---
title: "Gutsy Dell laptop with nvidia G440 Black Screen after drive update"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by mjcoury on 2007-10-19
I installed Gutsy, no issues, I went to turn on the wizbang eye candy, and it asked to turn on restricted drivers (which it installed after adding resources to the add apps section) 

After it downloaded and installed the NVIDIA drivers I rebooted to a nice black FU screen.

Any ideas?  It was working fine before I tried to turn on the restricted drivers / upgrade drivers

---

### Post by mjcoury on 2007-10-22
No? Nothing? Not even a Titter?

---

### Post by Doughsay on 2007-10-27
Same problem here... Anyone got any ideas?  The X server actually loads, no errors, the screen just doesn't come on, seems like a backlight issue maybe?  How can i find out?  It works fine with the open source nv drivers...

---

### Post by coolcar on 2007-10-27
> **Doughsay said:**
> Same problem here... Anyone got any ideas?  The X server actually loads, no errors, the screen just doesn't come on, seems like a backlight issue maybe?  How can i find out?  It works fine with the open source nv drivers...

Same problem of blank screen here :(  After I installed the Restricted nVIDIA driver on my gutsy and rebooted I got a blank screen. It is Toshiba Satellite Pro TE2100 with NV17 [GeForce4 420 Go]

I can load the recovery mode and load the non graphics environment.

I rolled back the change after reading some other posts by booting into the text environment and editing the file xorg.conf. 

cd /etc/X11
vi xorg.conf

located section entry for Device - Videocard and change the Driver from "nvidia" to "nv"

exit

I used vi text editor as gedit did not work for me ( gksudo gedit /etc/X11/xorg,conf  ) Maybe we can use some other editor ?

After rebooting I am able to go to the X - Gnome environment 

Systems -> Administration -> Restricted Drivers Management is now showing NVIDIA accelerated graphics manager not in use.

---

### Post by Ginigrace on 2007-10-27
I was attempting to upgrade my ancient Toshiba Satellite 2435-S255 to Gutsy and everything seemed to work well after the installation completed and the system came back up. I was offered an upgrade to the proprietary nvidia driver for 3d effects and a software modem. I took the nvidia propriety upgrade which seemed to install well, but when the system restarted the Ubuntu startup screen logo meter started and ran for a couple of seconds but then the screen went black and the system seemed to shut down. 

Help!

---

### Post by orn on 2007-10-28
Same problem on a Dell Latitude with GeForce Go440

---

### Post by mike00554 on 2007-10-28
I'm having the same issue in my Dell Inspiron 8200. The whole system is nice until I try to install the restricted drivers then the whole screen is blank after a reboot. I can still log onto the computer but no GUI. Does the 440go require legacy, or new glx drivers?

I remember reading somewhere that the 440go is best used with legacy drivers. I haven't seen any solutions to this so far thoguh. ](*,)

---

### Post by Ginigrace on 2007-10-30
Can you run Ubuntu from a live Disk and change the Nvidia driver back? If so could some helpful person tell us novices how?  Thanks!

---

### Post by Therion on 2007-10-30
Boot your PC.
From the GRUB menu hit "Escape".
Select "**Recovery Mode**" (you'll wind up at a system prompt).
From the system prompt:
```
 nano /boot/grub/menu.lst
```
Scroll down to the bottom of the page using the arrow key, past all the # signs until you come to the first line that starts with Kernel.  This will be a long line of code that runs off the end of your display.  Use the arrow keys to scroll to the end of that line where you'll find where it says **-ro -splash -quiet**
Remove the word splash.
Ctrl+X to save, confirm the overwrite and reboot.

When you reboot you will NOT get a splash-screen but will go straight to your desktop.  There are other threads that deal with getting your splash-screen back, but none of the suggestions worked for me.  Try searching on "Black +Screen" in Advanced Search for some suggestions on how to get your bootup splash-screen back.

---

### Post by flegory on 2007-10-30
Hmm...Maybe we should file a Gutsy bug report.

---

### Post by JC Casiano on 2007-10-31
Something I found a couple months ago when I went from Edgy to Feisty...  Try adding this option to the "Device" section:

Section "Device"
  identifier "nVidia Corporation NV17 [GeForce4 420 Go]"
  boardname "nVidia GeForce4 420 Go"
  driver "nvidia"
  ...
  option "UseDisplayDevice" "DFP"

I'm currently running 9643, but the black screen problem occured under 9639.  My laptop (Sony VAIO PCG-GRT100) would display a black screen unless this option was present, I haven't removed it since.

---

### Post by Jaco Du Toit on 2007-10-31
For what it's worth, the only way I could get the NVIDIA driver to boot properly on Gutsy on my Dell Latitude D630 (with Quadro 135M screen card) was to disable the splash screen as a previous poster suggested. 

Unfortunately I still had a huge problem with dual screens and DRI not working properly.

The only way I was able to fix that was to actually download the NVIDIA drivers from the NVIDIA site and run the install script from the command prompt as per: 

[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html")

---

### Post by flegory on 2007-11-03
> **JC Casiano said:**
> Something I found a couple months ago when I went from Edgy to Feisty...  Try adding this option to the "Device" section:

Section "Device"
  identifier "nVidia Corporation NV17 [GeForce4 420 Go]"
  boardname "nVidia GeForce4 420 Go"
  driver "nvidia"
  ...
  option "UseDisplayDevice" "DFP"

I'm currently running 9643, but the black screen problem occured under 9639.  My laptop (Sony VAIO PCG-GRT100) would display a black screen unless this option was present, I haven't removed it since.

Holy crap that worked!  Thank you so much man, I was begining to lose hope. :KS

---

### Post by waspbr on 2007-11-03
sorry for my noobness, but I just had the same problem with the same laptop, toshiba satellite 2435-S255. And I am really glad to here that there is a solution to the problem, since i kinda ended up reinstalling ubuntu.

The curious thing is that although I had a black screen, ubuntu would still run, I plugged in my desktops LCD and it worked... so i guess the laptop screen couldnt handle it?

In any case, here comes my noobness, what exactly did you do to solve this, as in what file did you modify.

I am kinda new to linux so please bear with me 

l8er

---

### Post by flegory on 2007-11-04
> **Therion said:**
> Boot your PC.
From the GRUB menu hit "Escape".
Select "**Recovery Mode**" (you'll wind up at a system prompt).
From the system prompt:
```
 nano /boot/grub/menu.lst
```
Scroll down to the bottom of the page using the arrow key, past all the # signs until you come to the first line that starts with Kernel.  This will be a long line of code that runs off the end of your display.  Use the arrow keys to scroll to the end of that line where you'll find where it says **-ro -splash -quiet**
Remove the word splash.
Ctrl+X to save, confirm the overwrite and reboot.

When you reboot you will NOT get a splash-screen but will go straight to your desktop.  There are other threads that deal with getting your splash-screen back, but none of the suggestions worked for me.  Try searching on "Black +Screen" in Advanced Search for some suggestions on how to get your bootup splash-screen back.

Getting the splash screen back was very simple.  Just go back into the file and add "splash" to the end of the kernel line you mentioned.  Just remember to use super user mode.  I like the graphical super user & editor.

```
ksudo gedit /boot/grub/menu.lst
```

---

### Post by markfinn on 2007-11-07
> **JC Casiano said:**
> Something I found a couple months ago when I went from Edgy to Feisty...  Try adding this option to the "Device" section:

Section "Device"
  identifier "nVidia Corporation NV17 [GeForce4 420 Go]"
  boardname "nVidia GeForce4 420 Go"
  driver "nvidia"
  ...
  option "UseDisplayDevice" "DFP"

I'm currently running 9643, but the black screen problem occured under 9639.  My laptop (Sony VAIO PCG-GRT100) would display a black screen unless this option was present, I haven't removed it since.

Worked for me on my Dell latitude with a [GeFroce 440 GO].  I'm guessing it means to use the LCD (Digital Flat Panel -- DFP) as the output device.  That's why it will show up on an external monitor still.


I switched to a VT, added it to my xorg.conf, switched back to the X "VT", hit CTRL-ALT-BKSP to restart x, and away I went.

Those currently at a black screen might have 2 immediate options: pres CTRL-ALT-F1 to get a VT, login and add the DFP line to your /etc/X11/xorg.conf file, or plug in a monitor and edit xorg.conf.

If you don't know what you're doing, try "sudo pico /etc/X11/xorg.conf" to edit the file from a VT. CTRL-X exits pico.  then switch back to the X terminal with ALT-F7, and restart X with CTRL-ALT-BACKSP


As a side note, it seems weird that the internal display is off, but switching to a VT enables it.  Gotta love linux/X display drivers.

---

### Post by JC Casiano on 2007-11-09
Oh, just wait 'til you start playing with Beryl...  I have a whole bunch of things you can add to make that work...

---

### Post by madmatrixz3000 on 2007-11-17
Please enlighten us on getting Beryl to work with these drivers.  Or does all the stuff before already fix beryl/compiz.

---

### Post by JC Casiano on 2007-11-20
I'll try to remember all the items I learned from various web sites, and I apologize to any authors for not giving credit.  Make sure that you've installed Beryl and Emerald successfully first.  I've tested this with NVidia versions 9631, 9639, and 9643.  Here's what I have...

In xorg.conf "Devices":

[INDENT]  driver "nvidia"
  option "UseDisplayDevice" "DFP"
  option "XAANoOffscreenPixmaps" "True"
  Option "UseEvents" "True"
  Option "DamageEvents" "True"
  Option "DisbleGLXRootClipping" "True"
  Option "AddARGBVisuals" "True"
  Option "AddARGBGLXVisuals" "True"
  Option "AllowGLXWithComposite" "True" 
  Option "backingstore" "true"
  Option "TripleBuffer" "True"
  Option "RenderAccel" "True"
  Option "DRI" "True" 
[/INDENT]

In these two sections:

[INDENT]Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  Option "Composite" "Enable"
  Option "DAMAGE" "Enable"
  Option "RENDER" "Enable"
EndSection
[/INDENT]


I stopped using beryl-manager, instead opting for a shell script. Create ".startberyl" in your home directory (you can actually call it anything you want and put it anywhere in the system that you have access to.  The period at the start of the filename just causes the filesystem to hide the file.):

[INDENT]#!/bin/bash

beryl --use-tfp --force-aiglx &
emerald --replace &
[/INDENT]

Once the file is created **change the permissions** so that it can be excuted.  I'm lazy, I did it from the file manager so I can't tell you what commands to type.

Edit ".profile" in your home directory, add the line "export KDEWM=~/.startberyl", though you should do this only AFTER you've tested .startberyl.

Now, some explanations.  I haven't tested all the Option parameters in the xorg.conf file so I don't know which ones really apply.  Having cobbled the information from various sources, I lost track of why they are there.  But since I managed to get Beryl working on a Go 420 with a meager 32MB of RAM I decided to leave well enough alone.

The .startberyl and .profile changes go hand-in-hand.  On the Go 420, I found that Beryl would only work correctly if I use "tfp" and "aiglx".  I played with many combinations and they either didn't seem to do anything or made things worse, and I settled on these because they work all of the time for me.  At least I have NOT had the "black window" problem (not the same as the black screen problem that started this thread).  

The commands in .startberyl can/should be executed manually to test with, just remember to use the "&" after each command or you'll have to open multiple terminal sessions (the "&" allows you to spawn a program and then return to the current session, otherwise you have to abort the program you just launched).  But I strongly recommend creating the script and letting it execute the commands because I sometimes lost keyboard control of my terminal sessions before I was able to run the "emerald" command and had to restart X.

The ".profile" addition exports the system variable KDEWM, and assigns the script .startberyl to it.  If KDEWM is not set, or set to an invalid program, "kwin" becomes your window manager.  I set KDEWM to run my script instead, which then launches beryl with emerald as the window manager.  This way I don't get a temporary black screen when I kill the kwin process as I load beryl and emerald.

Lastly, you might also want to create a script that kills beryl and emerald; the command is "killall <app>".  Why?  Well, GoogleEarth doesn't play with Beryl.  Neither do the GL screen savers.  I have World of Warcraft and Quake III Arena running under Wine, but they suffer performance issues when they are launced while Beryl is running.  I wrote a script that allows me to toggle beryl and kwin from the panel as needed.

In Beryl Settings Manager, avoid Transparency in your Desktop Cube configuration (this pertains to my Go 420 on my 2.2GHz P4-M and similar slower systems) if you get really bad response time in your sessions.  My guess is that we're losing large amounts of processor time as the system reverses and fades the previous desktop top snapshots to display them backwards through the current desktop's transparency.  Performance may get even worse if there is a video clip running on one of the back windows, but I haven't actually tested that.

---

