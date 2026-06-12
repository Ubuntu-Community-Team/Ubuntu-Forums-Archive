---
title: "Fresh install on Dell Inspiron 4000, video corrupt"
date: 2008-09-12
forum: Hardware
---

### Post by KR4WM on 2008-09-12
I was successful installing Kubuntu on my laptop, but that is where it ended. The screen was split into three overlapping pieces. I was able to fiddle with it long enough to get useable video by changing from the ATI Mobility driver (which should be the correct driver) to VESA (generic) driver, then increasing the screen size incrementally. I lost video again before reaching full screen size, but this time it was totally unusable so I had to re-install Kubuntu a second time. Still didn't work, so I decided to try Fedora. Fedora did the same thing as Kubuntu. I decided to go back to Kubuntu, as I could not move the windows around in Fedora to gain access to usable video. Then my laptop got stuck booting Fedora off the hard drive and refused to boot from the Kubuntu CD. I finally gave up and am re-installing Windoze. Hopefully after this is finished, I'll try re-installing Kubuntu for the third (or fourth) time! Has anyone else had a video driver issue with a Dell Inspiron 4000 and ATI Mobility integrated video card? Thanks, -Web in Myrtle Beach, SC

---

### Post by KR4WM on 2008-09-12
No luck. The re-install still gives me a screen split into three pieces with only part of a box readable, and the other part missing. I found System Settings/display, but the only selections there are the screen size (800 x 600 and 640 x 480) and refresh rate (56 and 60Hz). Changing any of these does nothing to fix the problem. I suspect changing from LCD to Standard monitor might fix the problem, but after spending several hours looking for this setting in the menus, I've come up empty handed. There is no box in the lower right corner to change to "admin" or "supervisor" settings or anything like that. Typing search expressions in HELP only wants to get on the internet for the search, but this laptop is not connected to the internet, and isn't going to be until I get the display issue fixed. It works fine in Windoze. I hate to uninstall Linux because I really wanted to learn it, but if I can't get a useable display out of this laptop, I have no otehr choice than to remove it and downgrade back to Windoze. HELP! Thanks, -KR4WM

---

### Post by KR4WM on 2008-09-12
Tried for the final time- I'm giving up. I could never get the screen to fill. I even tried an external monitor, and even it would not sync to Kubuntu. I guess the Dell Inspiron 4000 is not designed to run Linux, or at least not this version. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by KR4WM on 2008-09-12
I can't stand for things not to work! I spent another four hours on it, and finally have it "close". At least it's usable now. Now to get a PCMCIA Linksys wireless networking card to work...

---

### Post by ture on 2008-10-16
I have been able to get earlier versions of Ubuntu (up to and including 8.04) to work nicely on my Inspiron 4000 by

  1. Booting the install CD

  2. Switching to a text virtual console (ctrl-alt-f1)

  3. Editing the X server configuration file and inserting the following modeline for the monitor

       Modeline "1400x1050" 107.85 1400 1450 1500 1999 1050 1058 1070 1150

  4. Flipping back to the X virtual console (ctrl-alt-f7)

  5. Forcing the X server to restart (ctrl-alt-backspace).

(I cannot give more detailed instructions for step 3 at the moment, because I am at work and the computer is at home, turned off...)

These steps have given me a working graphic environment where I have been able to complete installation. After installation and reboot, repeating step 3 on the installed system has given me a permanently working system.

Unfortunately, this did not work for the 8.10 beta. Presumably I was editing the wrong config file (/etc/X11/xorg.conf, I believe) or there is some auto-probing overriding my configuration.

---

### Post by bkwillard on 2008-12-21
*"3. Editing the X server configuration file and inserting the following modeline for the monitor"*

I'd like to have more information on how to do this step.  I've been editing the /etc/X11/xorg.conf file like some threads tell me to do.  You say it's the wrong file.  I'm so confused...if you have time to give the details, I would appreciate it.

---

### Post by vermanium on 2009-03-11
Hi bkwillard
I have been trying to install linux on my inspiron 4000 with exactly the same display problem. I tried mint and i have found out thro google that the drivers wont work.
I was wondering if you could make this setup work? If so, would you be able to tell me? Thanks in advance.
Verm.

---

### Post by jdotsr1 on 2010-02-28
I was having the same trouble about initially only being able to get 800X600 resolution on Ubuntu 9.10 Karmic with my old I4000.  Then, I found an obscure post that helped me get to 1024X768.

The outline was:

> Use sudo apt-get install alien in a terminal session
After alien is installed -
> Browse to support.dell.com
> Goto Drivers and Downloads
> Goto the support page for the Dell 4000
> Select the driver set for "Red Hat Linux"
> Download the ATI Mobility Driver "ATIMP310.RPM"
> Copy from Downloads to Desktop
> Open a terminal session
> Change the directory to the desktop
> Use sudo alien -i atimp310.rpm

Try it and see if you like it.

---

### Post by Amberac on 2010-09-07
jdotsr1: Many thanks for the above resolution. Worked with my Dell Inspiron 4000 after much searching of forums.

Laptop is now usable again without using Win 2000 !! Fully Mint only.

Thank you  :D:D

---

### Post by neeero on 2011-09-07
Thanks for the great post. I can finally enjoy looking at the screen.
I am bit concerned about the perfomance though.
While i can get a DVD to play .. Youtube playback stutters. (i've even set it the lowest quality)
I've got the latest flash version but i guess its too CPU/Video demanding and the hardware just can't handle it.
Is there a way to squeeze more perfomance out of the video so that flash content can play without stutter?
Many thanks.

---

