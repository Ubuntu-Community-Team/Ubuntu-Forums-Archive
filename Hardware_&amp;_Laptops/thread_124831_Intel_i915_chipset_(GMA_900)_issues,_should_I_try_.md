---
title: "Intel i915 chipset (GMA 900) issues, should I try full Kubuntu install"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by hyperpsyched on 2006-02-02
I apologize for posting this in 2 spots but i first posted in Kubuntu (KDE) and I think that was the wrong location to start a laptop related (k)ubuntu thread.

oh boy...

First off let me say I really want to get Kubuntu 5.10 installed so baaaad (I can almost taste that minty (k)ubuntiness) but oh boy...

I am running a Toshiba M60 laptop, 17 " widesreen (so evetually I guess want 1200 X 800 res) with (gulp) the i915 chipset, meaning the intel gma 900 graphics acclerator. Well both ubuntu 5.10 and kubuntu 5.10 live cds are not working... and I am a little nervous going ahead with a full install without at least understanding why i am having problems. So here is as complete an explanation as I can provide.

I boot both cds and all seems well and good until the X server starts up. In ubuntu this causes this bluish error message to pop up and the output thereafter becomes pretty tough to read. In Kubuntu it just hoes to the command prompt. Either way both end up at the prompt. so I try start X and on both flavours and I get this:

***********

skipping "/usr/X11R6/lib/modules/libGcore.a: m_debug_clip.o" No Symbols Found
...
(same for m_debug_norm.o and m_debug_norm.o)
...

(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) I810(0): No video BIOS modes for chosen depth
(EE) Screen(s) found, but none have a usable configeration
Fatal Server Error: No Screens Found (ouchhhhhh!)
...blah, blah
XIO: fatal IO request 104 (Connection reset by peer) on V server "0:0" after 0 requests (0 known processed) with 0 events remaining


*************

Ok... that sucked a little bit.

I took a look at ny xorg.0.log file (seems to be the thing to do

****
..blah
(==) ServerLayout "Default Layout"
(**) |--> Screen "Default Screen" (0)
(**) | |--> Monitor "Generic Monitor"
(**) | |--> Device "Intel Corporation Default Card"
(**) |--> InputDevice "Generic Keyboard"
(**) " "Configured Mouse"
(**) " "Synaptics Touchpad"
(WW) the directory "/usr/share/X11/fonts/Cyrillic" does not exist. Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.

***

Ok... greek to me so then I checked out my org.conf file and all I found were directory locations for fonts... nothing else. Nothing mentioning any other type of hardware at all. Boo.

I typed in "man /etc/X11/org.conf" and everything, including the font locations was there, or so it seems. Any way it looks like this:

*****

Section "Module"
Load "GLove" // is this right? where is the special sauce
...
Endsection

Section "input Device"
Identifier "Configured Mouse"
...
Endsection

...some other sections for Keyboard, Synaptics Touchpad, etc...

Section "Device"
Identifier "Intel Corporation Intel Default Card"
Driver "i810" //is this the problem? I have the i915
BusID "PCI:0:2:0)
EndSection

Section "Montor"
Indentifier "Generic Monitor"
option "DPMS"
Endsection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Intel Default Card"
Monitor "Generic Monitor" Default Depth 16
.... wole bunch of ,Subsection "Display", here all with Modes "1440 x 900" and Depth values of 1 4 8 15 16 and 24.

Section "ServerLayout"
... all the stuff above in here.
Endsection

Section "DRI"
mode 0666 //this must be the problem, he devil's number!
Endsection

****

Should this file not be in my xorg.conf file?

So this is all I have. I have seen some forums for other linux distros with i915 probs and the fixes sound cryptic. What I need is a clear explanation of the problem and a pretty coherent answer to this question. Is it worth the hassle of installing Kubuntu 5.10 onto my harddrive as dual boot? Or am I stuck with XP, cry If I should go with the install what do I need and how do I install it? How easy are these fixes for a brave, if somewhat computer illiterate, newbie. I will try anything though as I figure if it messes up I can simply format the partition Linux is on an trytry again.

Please help me, I need Linux... I am already using Cygwin more than Windows and colinux nearly gave me an aneurism while trying to install.

Thanks from Hyperpsyched

---

### Post by darm on 2006-02-02
try using vesa drivers. you won't get video acceleretion or composite or anything, but you'll have solid 1280*800 on a working system and full ability to experiment. You might want to use sudo dpkg-reconfigure xserver-xorg if you are not sure what and where to put in xorg.conf.

It seems strange to me actually as my Acer with 915 chipset works in correct resolution with 5.10 livecd and vesa drivers are assigned automatically. I'm still strugling to get the accelerated video on a stable system though =)

---

### Post by hyperpsyched on 2006-02-02
Will try the Vesa drivers. I will go with the full install just to see how well I can get it working. I also have a synaptic touchpad which seems to cause some grief. Will see how many other gotchas I find.... Thanks though for the response... I no longer feel so very alone :D

---

### Post by mo_x on 2006-02-02
I have no first hand experience but have read in other threads that with a little tweaking it can be made to work. You probably need a program called 915resolution.

---

### Post by zachstruck on 2006-02-02
915resolution fixed my display resolution problems.  You just need to have the script run at start up.
Download it here: [http://packages.ubuntu.com/dapper/x11/915resolution]("http://packages.ubuntu.com/dapper/x11/915resolution")
Then, Open the terminal and type *sudo gedit /etc/init.d/bootmisc.sh* to edit the boot-up script.
Add **/usr/sbin/915resolution 58 1280 800** before ": exit 0" at the end of the script.
It fixed it for me at least.

---

### Post by hyperpsyched on 2006-02-04
Changed the driver to vesa and at least have a working desktop. I was so happy at that point I nearly peed myself. I am so exited I can barely type... anyway I will try to install the i955 resolution stuff though I heard this causes some probs abfter hibernation/standby. Head the 855(50?) resolution works better... anyway THANKS for all the input!!! Could't have done it without ya!

---

### Post by guano on 2006-02-17
I have a widescreen laptop with the same graphic card and I run 1280x800 just fine. I use the i810 driver on xorg.conf. You might want to search somethin on "modeline", and isert it into your xorg.conf. 

look at my xorg.conf:

```
Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection
```

I know that there's a site were you can determine the modeline for your LCD, there's a llink somewhere in this forum...

hope this helps..

---

