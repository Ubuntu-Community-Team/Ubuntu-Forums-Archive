---
title: "fiesty on sony vaio VGN-T240P laptop"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by ChrisNoXmas on 2007-08-19
Hi,

I am new to ubuntu. I installed it on my desktop PC where it worked perfectly out of the box so I decided to install on my Sony Vaio VGN-T240P with Intel GMM 855 video drivers. I was able to get the screen resolution fixed by updating the intel drivers, and I was able to get sound to work by configuring and installing ALSA on the machine. Now, however, I cannot get video to work (quicktime or avi). I have installed every driver I can think of and every driver recommended to me on the ´getting started´ section. Using VLC and MPlayer, I can load the video. I can hear the videos sound, however, in place of video I just see a BIG BLUE SCREEN.

Anyone have any experience with this?

Thanks so much,

Chris

---

### Post by ozgurcakmak on 2007-08-20
Dude... this is a codec problem. Install automatix and install codecs with it. Then you will be able to watch any video without any heartburn.

---

### Post by kerry_s on 2007-08-20
> **ChrisNoXmas said:**
> Hi,

I am new to ubuntu. I installed it on my desktop PC where it worked perfectly out of the box so I decided to install on my Sony Vaio VGN-T240P with Intel GMM 855 video drivers. I was able to get the screen resolution fixed by updating the intel drivers, and I was able to get sound to work by configuring and installing ALSA on the machine. Now, however, I cannot get video to work (quicktime or avi). I have installed every driver I can think of and every driver recommended to me on the ´getting started´ section. Using VLC and MPlayer, I can load the video. I can hear the videos sound, however, in place of video I just see a BIG BLUE SCREEN.

Anyone have any experience with this?

Thanks so much,

Chris

my guess is you have both plug-ins installed, you can only have 1 plug-in for 1 player. i would just uninstall all the plug-ins and use> [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
you can set it up to use several players, down load vids, etc...

---

### Post by ChrisNoXmas on 2007-08-21
> **ozgurcakmak said:**
> Dude... this is a codec problem. Install automatix and install codecs with it. Then you will be able to watch any video without any heartburn.

This solution did not work.  Having installed all the codecs provided automatix under a clean install -- the same result was produced -- blue screen with sound.

---

### Post by ChrisNoXmas on 2007-08-21
> **kerry_s said:**
> my guess is you have both plug-ins installed, you can only have 1 plug-in for 1 player. i would just uninstall all the plug-ins and use> [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
you can set it up to use several players, down load vids, etc...

i tried your solution with a clean install -- and it did not work.  Same result.

---

### Post by ChrisNoXmas on 2007-08-21
Just for people's information -- I got sound to work by:

No sound for laptop

Problem:
    No sound to headphones or internal laptop speaker.
Solution:

       1. Open volume control panel (e.g. double click volume applet icon)
       2. Select Edit and Preferences
       3. Check External Amplifier in Volume Control Preferences dialog if it is not already checked
       4. Close Volume Control Preferences dialog
       5. Select Switches tab in Volume Control window.
       6. Uncheck External Amplifier option
       7. Close Volume Control window

I got resolution to work by:

sudo apt-get install xserver-xorg-video-intel

Then edit your /etc/X11/xorg.conf and change the

Dirver "i810"

to 

Driver "intel"

by typing:

sudo nano /etc/X11/xorg.conf

Update:

I just got video to work!

I installed the automatix codecs

then on VLC:

Settings:Preferences: Video:  Output modules:

Change 'default' to 'X11 video output'

---

