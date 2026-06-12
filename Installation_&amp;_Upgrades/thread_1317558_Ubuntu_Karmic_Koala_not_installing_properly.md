---
title: "Ubuntu Karmic Koala not installing properly"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by rockinthesixstring on 2009-11-06
I might be doing something wrong, but I just can't seem to get this to work.

I just downloaded the Koala version of [Ubuntu Mini ]("https://help.ubuntu.com/community/Installation/MinimalCD")today and followed the steps located [here]("http://xbmc.org/wiki/?title=XBMCbuntu#Install_miminal_Ubuntu") to the letter.

I got all the way through to the reboot part and restarted the system. System boots up to a black screen. I cannot SSH in (even though I told it to install OpenSSH). I can't even ping the system.

Where might I have gone wrong?         

on top of this, if I press the restart button I am taken to this screen 

GNU Grub 1.97~beta4
* Ubuntu, Linux 2.6.31-14-generic
* Ubuntu, Linux 2.6.31-14-generic (recovery mode)
* Memory test (memtest86+)
* Memory test (memtest86+, serial console 115200) 
If I select either the first or second entry it appears to just sit there and do nothing.  It's hung.

---

### Post by Thomas1477 on 2009-11-06
I am also having this same problem.This is what I am getting after the unit reboots after the installation:
Grub loading
Error:no such device:d9d54e3f-ad23-41a3-96d9-bebfcb0a4c81
Failed to boot default entries
Press any key to continue...

If you press any key you get same error, if you press the enter key you get;
GNU Grub 1.97~beta4
* Ubuntu, Linux 2.6.31-14-generic
* Ubuntu, Linux 2.6.31-14-generic (recovery mode)
* Memory test (memtest86+)
* Memory test (memtest86+, serial console 115200) 

If you press enter to try to boot from the highlighted item you get nothing,if you press key you go back to:

Grub loading
Error:no such device:d9d54e3f-ad23-41a3-96d9-bebfcb0a4c81
Failed to boot default entries
Press any key to continue... 

Anyone have any ideas???

---

### Post by rockinthesixstring on 2009-11-06
That's not quite the same problem as mine.

I'm getting a blank screen (forever)


It's only when I do a hard reboot that i'm taken to that screen that doesn't seem to work

---

### Post by rockinthesixstring on 2009-11-06
Well I grabbed the Jaunty version and am getting the EXACT same results.  

My research is leading me to believe that this is a graphics card issue, though I have NO idea on how to solve it.  I'm using the onboard HDMI on my 630i Motherboard.

---

### Post by CaptainMorganNZ on 2009-11-07
I had the same problem, finally managed to get the problem solved!

When the GRUB is loading press ESC, then go into the netroot option.
Type in your username and password.
If you have any fglrx programs installed, remove them via aptitude or apt-get. If you don't, move onto the next step.
Install xserver-xorg-video-ati (sudo apt-get install xserver-xorg-video-ati)

reboot (press b)

Hope that this works for you! I'd already tried adding i915.modeset=0 to the kernal lines in the boot command AND starting "startx" from netroot.

---

### Post by skyiscrying on 2009-11-07
> **rockinthesixstring said:**
> I might be doing something wrong, but I just can't seem to get this to work.

I just downloaded the Koala version of [Ubuntu Mini ]("https://help.ubuntu.com/community/Installation/MinimalCD")today and followed the steps located [here]("http://xbmc.org/wiki/?title=XBMCbuntu#Install_miminal_Ubuntu") to the letter.

I got all the way through to the reboot part and restarted the system. System boots up to a black screen. I cannot SSH in (even though I told it to install OpenSSH). I can't even ping the system.

Where might I have gone wrong?         

on top of this, if I press the restart button I am taken to this screen 

GNU Grub 1.97~beta4
* Ubuntu, Linux 2.6.31-14-generic
* Ubuntu, Linux 2.6.31-14-generic (recovery mode)
* Memory test (memtest86+)
* Memory test (memtest86+, serial console 115200) 
If I select either the first or second entry it appears to just sit there and do nothing.  It's hung.
[COLOR=Blue]You might be better off downloading the 9.10 version on the Ubuntu main page. Last Saturday, I downloaded 9.10 and it was -in my opinion- not the real deal. Had heaps of trouble with it. Today, 7th Nov, I got another copy from the main page and so far so good with everything.[/COLOR]

---

