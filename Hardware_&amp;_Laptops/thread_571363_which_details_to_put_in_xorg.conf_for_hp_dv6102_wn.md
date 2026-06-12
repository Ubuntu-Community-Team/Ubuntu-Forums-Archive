---
title: "which details to put in xorg.conf for hp dv6102 w/nvidia geforce go 6150"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by doron387 on 2007-10-09
installed kubuntu feisty dualbooting w/winxp,
machine hp laptop dv 6102 ea i386
nvidia geforfce go 6150
on booting it first writes  '(very fast dissapearing) found bios bug 81[xxxxxxx]' then the progress bar runs, then few more fast lines (i have noticed the word 'log in'), then another progess bar (but without any movement in it), then it starts to write lines that say something like this :
[54.32xxxx]bcm43xx : Error : micronode "ccm43xx_micronode5.fw"not available or bad (loaded _or_ failed - i forgot what was written)
hese lines run   v e r y   slowly, 
if i alt+ctrl+f something i get the cmnd line and if i startx it writes in the end of the page :
XIO : fatal IO error 104 (connection reset by peer ) on xserver ":0,0" ....
does somebody know what i should write in the xorg.conf to have kubuntu boot untill the end on my machine ?

attached are the graphics card details screen shots (i am sorry but my winxp is on hebrew, so the experets will know to recognize the important details)

---

### Post by molly_001 on 2007-10-09
Shalom,

Funny note:  I just now Googled only this:  dv6102 ,
and the first google hit was your doron ubuntuforums inquiry from today, 10-09-2007.
Amazing!!  Also tells me that 6102 model was exclusive Israel/MidEast product.

All comments below are for using sudo dpkg-reconfigure xserver-xorg

  i810 is the adapter interface, it is on the same selection screen as 'nv' and 'nvidia' and 'ati' and 'vesa' ... there are about 30 choices, and i810 is one choice.

  pci bus is the numbered bus on which your graphics adapter is sitting.  The graphics is almost always 1:0:0 .  Should you change it?  No, I would not do so, yet.


  for asterick ... looks like this --> *

   on the screen for selecting resolution, 
you want asterick ( * ) only next to 1024x768 and lower, such as 800 x 600

 please choose 'simple' for monitor selection.  Then simply choose appropriate size, for instance choose 19-20 inch if you have 19-inch monitor.

  definitely choose 16-bit for color (and not 24) because the basic support in 32-bit machines is for 16-bit color  (still gives you millions of shades)  ... 24 often will not work when configuring/using X Window manager


We can work via Skype this evening (I am -8 hours to Israel)

---

### Post by cubeist on 2007-10-09
> **doron387 said:**
> installed kubuntu feisty dualbooting w/winxp,
machine hp laptop dv 6102 ea i386
nvidia geforfce go 6150
on booting it first writes  '(very fast dissapearing) found bios bug 81[xxxxxxx]' then the progress bar runs, then few more fast lines (i have noticed the word 'log in'), then another progess bar (but without any movement in it), then it starts to write lines that say something like this :
[54.32xxxx]bcm43xx : Error : micronode "ccm43xx_micronode5.fw"not available or bad (loaded _or_ failed - i forgot what was written)
hese lines run   v e r y   slowly, 
if i alt+ctrl+f something i get the cmnd line and if i startx it writes in the end of the page :
XIO : fatal IO error 104 (connection reset by peer ) on xserver ":0,0" ....
does somebody know what i should write in the xorg.conf to have kubuntu boot untill the end on my machine ?


First, don't worry about the bios bug that disappears...all hp laptops have that and it doesn't really mean anything... and it is fixed in gutsy.

Second, the stuff about the bcm43xx is your wireless card, not graphics.  Obviously the system is trying to load a module that it doesn't like... don't worry about that for now... once you get into your system this link should help get your wireless going
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

Lastly, here is the output from my xorg.conf from my hp laptop with a 6150:
Section "Device"
        Identifier      "nVidia Corporation C51 [Geforce 6150 Go]"
        Driver          "nvidia"
        Busid           "PCI:0:5:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

You could try that ... it may boot, but I would change "nvidia" under the driver category to "vesa"

good luck

---

