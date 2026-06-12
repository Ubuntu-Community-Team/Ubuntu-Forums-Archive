---
title: "Jaunty - Compiz no longer works, ThinkPad T61 - Worked in 8.10"
date: 2009-04-23
forum: Hardware
---

### Post by raintheory on 2009-04-23
Hey all, 

Just did a fresh install of Jaunty (moved from 8.10), and now when I try to enable visual effects, I get the vague message: 'Desktop effects could not be enabled'.

Compiz and all worked great on my 8.10 install, anyone know why this could be happening with a fresh 9.04 install?  Anyone experienced something similar?  Any workarounds?

Thanks in advance!

-aA

---

### Post by raintheory on 2009-04-24
Got this straightened out with help from replies on a [similar post]("http://ubuntuforums.org/showthread.php?t=1134323").  Seems the Intel X3000 and X3100 graphics adapters have been blacklisted on purpose.  I have enabled them via the workaround below with no ill effects (yet):

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Logout, login again and then enable.  Did the trick for me.

Courtesy of [zman14321's post]("http://ubuntuforums.org/showpost.php?p=7129915&postcount=8") in the thread mentioned above...

Thanks!

---

### Post by jcookeman on 2009-04-27
Nice one! I had same problem on x61s.

---

### Post by namdung on 2009-04-29
Same issue in DELL Vostro 1500. Resolved now. Thanks.

---

### Post by ashleywiz on 2009-04-29
GREAT!!! this quick fixed worked wondereds for me on my thinkpad R60... fixed and got my compiz running again.. thanks
Ashley

---

### Post by jordey24 on 2009-04-29
Thanks,that worked great! =D

-jordey24

---

### Post by berov on 2009-04-30
Worked for me too. Thanks very much!!!

MSI Notebook VR601
Mobile GM965/GL960 Integrated Graphics Controller

---

### Post by crunchfighter on 2009-04-30
Yahtzee!!!!!

Worked great on 64 bit 9.04 running on a Gateway M-Series.

---

### Post by densou on 2009-04-30
were you affected by blacklisting on both EXA and UXA ? :confused:


I hadn't that issue, thankfully :)

---

### Post by Nechi on 2009-04-30
Gonna try this on my Compaq C700 laptop.

---

### Post by SilverDrake11 on 2009-04-30
You're a lifesaver. Had the same problem on a fresh 64bit jaunty install on my X61, and the code fixed it. But, hey, what happened to the restricted drivers manager? I definitely remember having nvidia restricted drivers on intrepid when I had that installed. Do I not need it or what?

---

### Post by MaindotC on 2009-05-01
How did you install or set your video configuration?  The x1300 on the T60 is no longer supported by ATI so I can't install the proprietary driver.

---

### Post by Nechi on 2009-05-04
It worked!!!!!  Thank you, thank you, thank you!!!!

---

### Post by MaindotC on 2009-05-04
bump - anyone have an answer to my question?

---

### Post by densou on 2009-05-04
have you tried the OpenSource drivers ?

package should be named 'radeon-hd' or similar

[pardon, I have an Intel crap :P ]

---

### Post by MaindotC on 2009-05-04
Yes I have xserver-xorg-video-ati installed but the wiki says:
> From Ubuntu 7.10 and onwards, the driver and server autodetect most settings. You can often just take away your xorg.conf and it will run fine.
So where are the settings if they're not in xorg.conf?  I tried "man radeon" and it's difficult to determine which settings I need, and even so I'm not sure where to put them.  I'm looking for some guidance in configuring an x850 card for ideal use.  Right now, it is UNBELIEVABLY slow and choppy with no changes and if I add anything to xorg.conf I can't boot into the desktop environment.

---

### Post by Legazy on 2009-05-04
I'm a little late, but wanted to say this works like a charm on my ThinkPad T61.

---

### Post by nbotticelli on 2009-05-06
Worked great on my mother's Thinkpad T61 with intel GM965 graphics.

What did the line
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
``` actually do? It makes Compiz skip checking for the correct driver from Intel? It doesn't actually change any kernal/drivers at all correct? So why the complicated set of instructions in Media and Audio forum?

Also, does the T400 with Intel graphics suffer from the same issue and will this code fix that too?

---

### Post by tormaser on 2009-05-21
great..! i have a HP dv6000 and now it's working perfect, tanks 4 this post.

---

### Post by MaindotC on 2009-05-22
bump - please answer my post?

---

### Post by namdung on 2009-05-27
> **namdung said:**
> Same issue in DELL Vostro 1500. Resolved now. Thanks.

The issue was resolved but soon my Laptop started to freeze. I have disabled compiz now and its working fine.

Maybe I'll have to wait till 9.10 for this bug to be fixed.

---

### Post by Potters Son on 2009-06-01
> What did the line

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

actually do? It makes Compiz skip checking for the correct driver from Intel? It doesn't actually change any kernal/drivers at all correct? So why the complicated set of instructions in Media and Audio forum?
nbotticelli, this code appears to create a configuration file in your home folder which says to skip checking the drivers to see if they're compatible. No kernel modification required ;), but you may have to run this command for every user on your computer that wishes to use Compiz :(.

> So where are the settings if they're not in xorg.conf?
strAlan, the fact that xorg now tries to autoconfigure itself annoys me too. However, this doesn't mean that xorg totally ignores xorg.conf, either. For example, [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904) -- in the "Performance regressions on Intel graphics cards" section -- indicates that X11 still reads xorg.conf and considers it a manual override for its automatic configuration. Just because your xorg.conf doesn't say anything doesn't mean it's being listened to. :)

I did some snooping in Synaptec; it appears that the closed-source fglrx driver for your system is provided in the package xorg-driver-fglrx. This is not installed by default on my system, but then again, I have an Intel chipset. Go into Synaptec and see if it's installed on yours. To select whether or not to use restricted drivers, press Alt-F2, type jockey-gtk, and hit run.

If you can't enable the driver there, you may have to consult [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), which tells you how to install the closed-source (faster) driver, or [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), which tells you how to install the open-source driver, which Ubuntu uses by default.

Godspeed, and I hope this helps.

---

### Post by miiko on 2009-06-06
Folks,

Just performed an install of Jaunty 64bit on my thinkpad t61. I have the nvidia card. Install went somewhat smoothly, although it didn't automatically restart. I had compiz working under my last install, Gusty 32 bit. Tried to enable effects. It seemed like it was trying to install the drivers, but just hung. Same thing with system->administration->hardward drivers. Just hangs.
Tried Envyng. It (the application) seems to either hang or crash.

Any thoughts? thanks in advance.

---

### Post by miiko on 2009-06-06
> **miiko said:**
> Folks,

Just performed an install of Jaunty 64bit on my thinkpad t61. I have the nvidia card. Install went somewhat smoothly, although it didn't automatically restart. I had compiz working under my last install, Gusty 32 bit. Tried to enable effects. It seemed like it was trying to install the drivers, but just hung. Same thing with system->administration->hardward drivers. Just hangs.
Tried Envyng. It (the application) seems to either hang or crash.

Any thoughts? thanks in advance.

Well, seems like all I needed to do was run Envy with the install CD in the drive. Works great now!

---

### Post by charkear on 2009-06-18
Worked for me!!

---

### Post by sdowney717 on 2009-06-22
did not work for me.
still no compiz
[CODE]scott@scott-desktop:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
scott@scott-desktop:~$ metacity --replace
/usr/share/themes/aquadreams/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/aquadreams/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/aquadreams/gtk-2.0/gtkrc:105: Murrine configuration option "style" is not supported and will be ignored.
/usr/share/themes/aquadreams/gtk-2.0/gtkrc:157: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "switch_windows"/CODE]

---

### Post by MaindotC on 2009-06-23
I just did the ol' fresh, clean install and I'm just sticking w/ Hardy b/c I won't be getting a faster graphics card anytime soon.

---

