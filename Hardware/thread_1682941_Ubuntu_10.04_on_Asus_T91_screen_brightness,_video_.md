---
title: "Ubuntu 10.04 on Asus T91: screen brightness, video playback, touch input when rotated"
date: 2011-02-06
forum: Hardware
---

### Post by onebir on 2011-02-06
I've been following the instructions here: [http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt](http://wiki.eeeuser.com/ubuntu_9.10_on_the_t91_t91mt) to install Ubuntu 10.04 on an Asus T91 (not an MT). Much of it is working nicely (right away or following the suggested tweaks), but some problems remain that I haven't been able to solve so far. Advice would be much appreciated.

1) Screen brightness. Although the backlight keys were working ok just after I installed Ubuntu, for reasons I don't understand they stopped working. The wiki page suggests a change in /etc/default/grub, but this doesn't seem to help either. This command:
```
xrandr --output LVDS0 --set BACKLIGHT 20
```
does reduce the screen brightnes, and after using it once the backlight keys work to some extent.

I tried adding "xrandr --output LVDS0 --set BACKLIGHT 20" to /etc/rc.local so that it would be executed on startup, but this doesn't seem to work. [I]Is there any way I can get this command executed automatically on startup?

[/I]2) Video playback. I followed the steps in "The Ubuntu Wiki Way", ie installed the GMA500 drivers & gnome-mplayer ; video playback of some xvids was jerky, so I decided to try to add the VAAPI support & followed the subsequent steps. After this the video files I was previously able to play jerkily no longer worked at all. I searched a bit & discovered a tool called used Ubuntu-Tweak ([http://www.howtogeek.com/howto/29584](http://www.howtogeek.com/howto/29584)) that can remove PPA depositories &/ rollback to earlier software versions. I used it to get rid of the "nvidia-vdpau/cutting-edge-multimedia" PPA repository & reinstalled mplayer (which I thought with the PPA disabled would now be the pre-VAAPI version & therefore work...) But I still can't play the same videos. I've also fiddled with the mplayer.conf file (adding & removing "vfm=xvid" & "vaapi" from the "vo=") line. *How can I restore the level of video support I had originally?*

3) Touch input in rotated screen mode. The script changes for activating the screen rotate button worked nicely, but the code to "Fix rotate touchscreen input", appended right at the end of /etc/acpi/rotatescreen.sh, (ie so that "esac" is the last thing in the file) doesn't seem to work. [I]Any idea how to fix this?
[/I]
There are a couple of other minor problems/areas I haven't checked (ie webcam, mike) -  the three above are the important ones for me... Any/all suggestions would be much appreciated - thanks!

---

### Post by onebir on 2011-02-07
1) Fixed (/worked round) the backlight problem. I added 
```
xrandr --output LVDS0 --set BACKLIGHT 20
```using System>Preferences>Startup Applications. (Click "Add", give it a name & enter the code above as the command.) The function keys work after this, but don't always span the full range. I also added the same command to a panel launcher for getting the brightness right down (where I need it).

BTW, does anyone know which file "Startup Applications" modifies? I tried half a dozen without success. (including /etc/gdm/PreSession/Default, /etc/gdm/PostLogin/Default, /etc/gdm/Init/Default)

---

### Post by onebir on 2011-02-07
Re 3 (touchscreen in rotated mode) - the rotate button stopped working.  No idea why. I ran xev and there was no response, so I gave up on the  button & set up a launcher for the script (ie  /etc/acpi/rotatescreen.sh, based on the wiki linked above, incorporating  the code from the  "Fixing broken rotation script & permissions"  & "Fix rotate touchscreen input").

This does rotate the  screen & when the screen is inverted the cursor tracks correctly.  When the screen is rotated 90 or 270 deg, the cursor moves in the same  direction as movements on the touchscreen, but it's displaced from the  point where the screen is actually being touched. The error also varies  depending on where the screen is touched :cry:

Any ideas or solutions for this? It's only really this (& to a smaller extent the problem with xvid playback) that's keeping me from getting rid of the windows partition. Very frustrating.

---

### Post by inearlygaveup on 2011-02-08
Not sure if your screen brightness/glare is the same as mine was but I found Redshift worked for me.

---

### Post by onebir on 2011-02-08
Thanks inearlygaveup - looks like that might be a very useful piece of software for dealing with screen-induced eye fatigue etc.

---

