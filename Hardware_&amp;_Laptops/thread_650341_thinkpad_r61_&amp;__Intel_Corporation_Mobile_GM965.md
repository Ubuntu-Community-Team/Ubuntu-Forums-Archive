---
title: "thinkpad r61 &amp;  Intel Corporation Mobile GM965/GL960 no tv out"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by NiN on 2007-12-26
Hi!

I'm trying to get the tv out of a thinkpad r61 to work.

It has an integrated intel chip (GM965/GL960).

When using xrandr, no TV out option is shown, only the external VGA (Which works well).

I searched the net for some howto to get it working, but was as of this time unsuccessful in doing so.

Maybe you can help?

[Edit]
I've filed a bug report. See [https://bugs.launchpad.net/ubuntu/+bug/178910](https://bugs.launchpad.net/ubuntu/+bug/178910)

---

### Post by sodalis on 2007-12-27
hi

im having quiet a similar problem with my thinkpad r61e and that chip.

the basic functions seam to work very well but i would like to activate the 3d options!

if i try to activate them i get an error telling me that it would not be possible!

i can not find a proper solution on google for that chipset so i can only hope to find some help here.

thanks a lot
sodalis

---

### Post by NiN on 2007-12-27
For using compiz and other things I've found and added the (missing) things necessary to thinkwiki.

Have a look at [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_R61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_R61)

---

### Post by sodalis on 2007-12-27
hi 

thank you very much for that update!

i tried my best to come allong but i suppose i am in bigger trouble now than before.

i tried everything to get thsi running: 

> Default installation will not be able to enable compiz becasue of the way the Intel chipsets work. I have found the following script to get around it (credits to the original author). Save the file as .sh and run it once to confirm you can get the compiz effects. You can add the file to your "Gnome Session" for subsequent reboots. q

#!/bin/sh
SKIP_CHECKS=yes compiz --replace

A better way is to edit the file </etc/compizconfig/config> and add the option there.

# /etc/compizconfig/config
<SKIP_CHECK=yes> 


This way the setting will be available for all users of the laptop. 

but i couldent activate the visual effects allthough glx has been activated 

when i typed compiz into the terminal the entire terminal broke down 

than i realised that instead of the intel there was a vesa running in display properties. so i switched it to intel 965 an made a restart.

after reboot i got some grafik problems but through klicking on ok i finally made the login and now everything seams to run normal.

but if i make glxinfo i get:

> name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

what has happend?
how can i solve this problem?

i just dont get it :(

best wishes
sodalis


ps: here is the error i get when i type compiz into the terminal:

Checking forxgl: not present
no whitelisted driver found
aborting and usingfallback: /usr/bin/metacity

---

### Post by NiN on 2007-12-27
Sorry, I had a irritating description in the wiki.

Simply do the following:
```

sudo echo "SKIP_CHECKS=yes" >>/etc/compizconfig/config

```

Then check in the /etc/X11/xorg.conf file, that the driver for your graphic card is the intel one.

The entry should look similar to this example:
```

Section "Identifier"
  Identifier  "A name for the card
  Driver     "intel"
  ...
EndSection

```

and then try to enable compiz.

---

### Post by sodalis on 2007-12-27
thank you very much for the quick reply!

if i enter the first code into the terminal i get the following (allthough i intentionally opend that file with sudo short before in order to have proper rights):

> sodalis@sodalis-thinkpad:/etc/compizconfig$ sudo echo "SKIP_CHECKS=yes" >>/etc/compizconfig/config
bash: /etc/compizconfig/config: Permission denied
sodalis@sodalis-thinkpad:/etc/compizconfig$ 



it works only with:
> SKIP_CHECKS=yes compiz

and than only for a couple of time and with lots of errors, like windows can only be closed using alt plus f4 etc

---

### Post by NiN on 2007-12-27
Hi!

2 things here:
  - I can't reproduce the echo error here, but that is no big problem.
  - The vesa entry is indeed your problem :)

So to get things working:
  - if you get this permission denied error, try it this way:
```

sudo apt-get install libcompizconfig0
sudo gedit  /etc/compizconfig/config

```
 - Now enter the SKIP_CHECKS=yes line in the gedit window at the end of the file.
 - To get the intel driver, just replace vesa with intel.

btw: it's a good idea to instal compizconfig-settings-manager to adjust compiz settings.

---

### Post by sodalis on 2007-12-28
hi 

allready solved that vesa problem.

thanks again for the codes! did all that and installed some further x server packages. now i can boot with x and compiz enabled. 

but most effects just dont work as they should!!
for example thr cube somtimes changes to normal sliding windows or just regretts to turn when the mouse reaches the edge of the display.
other effects dont appear after activating. and the alt+f4 problem still appears with out any rule (at least i cant see it) :confused:

ps: i am using compizconfig-settings-manager

---

