---
title: "How to enable lower screen resolutions"
date: 2013-04-18
forum: Hardware
---

### Post by ikmailnaarjou on 2013-04-18
Hi there,

I have a problem to enable a lower screenresolution.
My laptop is a HP elitebook8730w with NVIDEA Quadro FX2700M video card, latest drivers installed.

I give a lot of presentations, so a lower screenresolution on a beamer is verry importand to me.

I have updated the driver last week, and now i am unable to set my screenresulotion to a lower resolution.
I use the tool *disper *to set the resolution, but now it give me not the right resolution.

**The output of disper -l**
*user@ubuntu12:/etc/X11$ disper -l*
*display DFP-0: LGD*
*resolutions: 1920x1200*

Normaly it gives me a lot of different resolutions, now only the highest.

**The output of xrandr:**
*VGA-0 disconnected (normal left inverted right x axis y axis)*
*LVDS-0 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 367mm x 230mm*
*   1920x1200      60.0*+*
*DVI-D-0 disconnected (normal left inverted right x axis y axis)*
*HDMI-0 disconnected (normal left inverted right x axis y axis)*

I allready tried to edit xorg.conf to add a rule to the section *screen *and reboot, but it did not help:

*Section "Screen"*
*    Identifier     "Screen0"*
*    Device         "Device0"*
*    Monitor        "Monitor0"*
*    DefaultDepth    24*
*    Option         "NoLogo" "True"*
*    SubSection     "Display"*
*        Depth       24*
***        Modes      "1280x1024"  "1024x768" "1152x864" "1920x1200"  "1920x1080"***
*    EndSubSection*
*EndSection*


I have tried to add a resolution with xrandr, but that allso didn't work

*user@ubuntu12:/etc/X11$ xrandr --addmode LVDS-0 1920X1080_60.00*
*xrandr: cannot find mode "1920X1080_60.00"*



Can sombody tell me how do i get the lower resolutions back?

(i am sorry for my bad englisch, i am a dutch [IMG]http://ubuntuforums.org/images/icons/icon12.png[/IMG] )

---

### Post by ikmailnaarjou on 2013-04-22
Is there realy nobody thats know the solution?

---

### Post by Tim Bob on 2013-04-22
Ok..dunno if this will work but ctrl alt + and ctrl alt - should rotate through resolutions known to the server.

---

### Post by ikmailnaarjou on 2013-04-22
> **Tim Bob said:**
> Ok..dunno if this will work but ctrl alt + and ctrl alt - should rotate through resolutions known to the server.

I have tried it, but xrandr -q still does not show me all the possible resolution.
Some other ideas?

---

### Post by Tim Bob on 2013-04-22
> **ikmailnaarjou said:**
> I have tried it, but xrandr -q still does not show me all the possible resolution.
Some other ideas?
  
Can you roll back the driver or contact the driver author ?

---

### Post by ikmailnaarjou on 2013-04-22
Yes, I did, didn't help. I rolled back 3 drivers, nothing helped.
I am getting crazy about this.

---

### Post by Tim Bob on 2013-04-22
> **ikmailnaarjou said:**
> Yes, I did, didn't help. I rolled back 3 drivers, nothing helped.
I am getting crazy about this.

If you know where the drivers were located on disk see if you can find all files in that subtree that have a modified date since you updated driver. Make a note of those files and look for the same files on your install media or maybe have someone you know with the same release give you a copy (or ask here perhaps). I assume no dumps done prior to upgrade where you could do an incremental and see files modified in filesystem since epoch.

Have you read this page [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) about configuring different resolutions? Doesnt really talk about nvidea. You had the beamer on when you ran disper?

Check out the disper page at the author's site [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/) and at the bottom of the page contact him and ask the right questions.

---

