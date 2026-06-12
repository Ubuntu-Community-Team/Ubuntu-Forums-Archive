---
title: "TouchPad issue"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by John.Michael.Kane on 2005-10-13
Same touchpad issues. making this "final" unusable

good luck to all who are using this

---

### Post by GrumpyBob on 2005-10-13
What are the touchpad issues?

Robert

---

### Post by John.Michael.Kane on 2005-10-13
Slide bar in all programs dont work double tap problems you cant drag the slide bar up and down. can't drag your pointer over text to copy. i have posted this issue on buzilla. there has been no fix. for me breezy is broken cause of this.

Good luck to all who upgrade

---

### Post by ajaustin on 2005-10-13
What touchpad are you using?  My Synaptics Touchpad works fine.

---

### Post by John.Michael.Kane on 2005-10-13
Touch pad works fine in 5.04. I dont see where what kind it is matters. happy however your's works.

almost all touchpad's are Synaptics/alps

---

### Post by ajaustin on 2005-10-13
Attached is my xorg.conf file in case it is of any help to you.  I have disabled tapping because I just can't cope with it, too clumsy!

---

### Post by civilwarlord on 2005-10-13
[QUOTE=ajaustin]Attached is my xorg.conf file in case it is of any help to you.  I have disabled tapping because I just can't cope with it, too clumsy![/QUOTE]


This may be a stupid question, but is the "MaxTapTime" part where you disabled tapping?

---

### Post by John.Michael.Kane on 2005-10-13
ajaustin thanks however your xorg file broke the install.

---

### Post by Czubek on 2005-10-13
I have the same problem as SD-Plissken.
My touchpad works fine under 5.04.
My laptop is Toshiba Satellite 1800.

---

### Post by John.Michael.Kane on 2005-10-13
I dont expect it to be fixed anytime soon... 

Good luck to all who install it.

---

### Post by ajaustin on 2005-10-13
[QUOTE=civilwarlord]This may be a stupid question, but is the "MaxTapTime" part where you disabled tapping?[/QUOTE]

Yes, there is a home web site for the Synaptics driver that I found.  Not sure where at the moment, but it has more info on the driver than I could possibly understand.:D

---

### Post by civilwarlord on 2005-10-13
[QUOTE=ajaustin]Yes, there is a home web site for the Synaptics driver that I found.  Not sure where at the moment, but it has more info on the driver than I could possibly understand.:D[/QUOTE]


Thanks, that stupid touchpad was bugging me.

---

### Post by John.Michael.Kane on 2005-10-13
Has anyone sloved this issue?
@civilwarlord was you able to fix your touchpad
@Czubek did you fix yours

I dont think it will be fixed anytime soon.. if you how ever have got yours to work thats good.

---

### Post by civilwarlord on 2005-10-13
[QUOTE=SD-Plissken]Has anyone sloved this issue?
@civilwarlord was you able to fix your touchpad
@Czubek did you fix yours

I dont think it will be fixed anytime soon.. if you how ever have got yours to work thats good.[/QUOTE]


My touchpad always worked, I just hated how sensitive to tapping it was.

---

### Post by John.Michael.Kane on 2005-10-13
oh ok well. i guess this issue can not be fixed. shame. 5.10 is unuseable..like this.
5.10 is broken so it's back to 5.04 hope the dev's fix this issue by the time the release the final version of drake. i dont feel they will fix this issue now. 

good luck all who use this "final"

---

### Post by Pausanias on 2005-10-13
Don't be such a pessimist. This will get drag-and-drop working:

```

sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"

```

Then reboot.

---

### Post by John.Michael.Kane on 2005-10-13
pessimist no. just telling what i feel. thanks for your idea. will test it and see.

Edit: if what you posted does fix it then why is not fixed by default

---

### Post by DrMoxie on 2005-10-13
Same boat here with a Toshiba Satellite 2400-S251; touchpad jumps all over and no scroll events are handled.  External mouse works fine, though.  Like SD-Plissken, the tough pad has worked fine for me from 4.10 and 5.04 with no tweaking.  Both the upgrade and clean install have resulted in the same problem.  I would love to have a fix for this but I am hesitant to play with the xorg config as I don't want to cause more problems for myself.  ;)

---

### Post by John.Michael.Kane on 2005-10-13
sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe" then reboot

The above code Does work.. only problem is that if you reinstall5.10 you have to type that code again in the terminal to fix the issues.


@Pausanias Thank you. hope the de'vs get this fixed soon

---

### Post by GreatBunzinni on 2005-10-14
[QUOTE=SD-Plissken]ajaustin thanks however your xorg file broke the install.[/QUOTE]

I believe the objective was not to replace your xorg file but to read it and compare the differences in the touchpad definitions.

---

### Post by John.Michael.Kane on 2005-10-14
the issue has been fixed. untill you reinstall. then you just have to use the code posted above again.

---

### Post by Czubek on 2005-10-14
[QUOTE=Pausanias]Don't be such a pessimist. This will get drag-and-drop working:

```

sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"

```

Then reboot.[/QUOTE]

Thanks, it works on my tosh.

---

### Post by Pausanias on 2005-10-14
[QUOTE=SD-Plissken]if what you posted does fix it then why is not fixed by default[/QUOTE]

Probably too many different pieces of hardware, too little time to test them all. Or not enough $$$ to try it our on the newest systems. Though you would think that they'd try hard to at least get the newest Dells and Toshibas working properly.

I'm glad I've stuck with Ubuntu---it's the best Distro once it's working. But I haven't had an easier time installing it than the others, that's for sure.

What they should do is have a bootup screen that says: did you have trouble with hardware last time you ran me? Then press F1. Then it guides you through a menu, so that it automatically regresses you from the latest fancy-but-broken drivers to the basic-but-working drivers for whatever device was giving you trouble.

---

### Post by Pausanias on 2005-10-14
An update from the Breezy development thread. If proto=exps does not work for you in the above, try proto=any instead. Thanks to Cozon.

---

### Post by DrMoxie on 2005-10-15
[QUOTE=Pausanias]An update from the Breezy development thread. If proto=exps does not work for you in the above, try proto=any instead. Thanks to Cozon.[/QUOTE]

Thanks, but no luck for me with either; the cursor still skips about the screen and the scroll events only scroll up. :(  

Being pretty new to linux (10 months on Ubuntu 100% of the time), I'm curious as to what exactly changed between 5.04 and 5.10 with regards to touchpads.  Is it a driver that I can roll back or something I just need to grit my teeth and hope for an update?  The touchpad worked perfectly under 4.10 and 5.04.  TIA!

---

### Post by Hezekiah on 2005-10-15
If you have an Alps touchpad rather than a Synaptic, then Breezy has "better" support for it out of the box than Warty/Hoary.  The problem is, this better support requires manual tweaking to get extra things working (scrolling, both circular and otherwise, less sensitive tap-click, others).

For Alps pads, which do act quite different from Synaptics pads apparently, Warty/Hoary would generally fall back to treating the pad like a normal PS2 mouse.  The pad itself would then take care of some of the extras like double-click-drag and other items on its own.  I think you can force this in Breezy, but I have not tried it.

---

### Post by tictoc on 2005-10-15
[QUOTE=Pausanias]Don't be such a pessimist. This will get drag-and-drop working:

```

sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"

```

Then reboot.[/QUOTE]
Thank you very much

---

### Post by cybazyrfa on 2005-10-16
Hello Pausanias!

Thanks a lot for this solution to the problem (drag and drop, click and drag, scroll bar not working on notebook / laptop with touchpad):

sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"

It just works perfectly! =)  This hint helps so much more than 'whishing 10 times good luck'...

Enjoy your Ubuntu! It's great. It's free! If you don't like it - you don't have to use it ;)

( Acer Travelmate 290 LCi with ALPS Touchpad Pointing Device ).

---

### Post by kvidell on 2005-10-16
What kind of touchpads are in ThinkPad laptops?
Mine's worked perfectly out of the box in Hoary and Breezy... better in Breezy than in Hoary though.
In Breezy I could do edge-scrolling out of the box, I couldn't even do that in windows.
It's tap sensitivity is also pretty much perfect for me.
- Kev

---

### Post by iteachgeeks on 2005-10-16
[QUOTE=SD-Plissken]Same touchpad issues. making this "final" unusable

good luck to all who are using this[/QUOTE]

The following instructions are for breezy

Download  the ([latest synaptics source]("http://web.telia.com/~u89404340/touchpad/files/")) and run make to create a new synaptic_drv.o. (You need X11-devel to do that.) Then  replace file in /usr/X11R6/lib/modules/input with the new one.

Add/edit the following lines in xorg.conf then restart X.

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
	Option		"LeftEdge"		"120"
  	Option		"RightEdge"		"830"
  	Option		"TopEdge"		"120"
  	Option		"BottomEdge"		"650"
  	Option		"FingerLow"		"14"
  	Option		"FingerHigh"		"15"
  	Option		"MaxTapTime"		"180"
  	Option		"MaxTapMove"		"110"
  	Option		"EmulateMidButtonTime"	"75"
  	Option		"VertScrollDelta"	"20"
  	Option		"HorizScrollDelta"	"20"
  	Option		"MinSpeed"		"0.3"
  	Option		"MaxSpeed"		"0.75"
  	Option		"AccelFactor"		"0.015"
  	Option		"EdgeMotionMinSpeed"	"15"
  	Option		"EdgeMotionMaxSpeed"	"15"
  	Option		"UpDownScrolling"	"1"
  	Option		"CircularScrolling"	"1"
  	Option		"CircScrollDelta"	"0.1"
  	Option		"CircScrollTrigger"	"2"
EndSection

---

### Post by RSX311 on 2005-10-16
[QUOTE=iteachgeeks]The following instructions are for breezy

Download  the ([latest synaptics source]("http://web.telia.com/~u89404340/touchpad/files/")) and run make to create a new synaptic_drv.o. (You need X11-devel to do that.) Then  replace file in /usr/X11R6/lib/modules/input with the new one.

EndSection[/QUOTE]

Where do I get the X11-devel? I tried to type "make" but bash said command not found.  I tried to look in the Synaptic Package Manager but its not there.

Thanks

---

### Post by tetsuo29 on 2005-10-17
The packages that need to be installed are:
- x-dev
- libx11-dev
- libxext-dev

Also, after I installed these packages, I kept getting compile errors like:
/usr/include/X11/Xlib.h:3575: error: syntax error before &#8216;_X_SENTINEL&#8217;

A google search turned up the following:
([http://lists.freedesktop.org/pipermail/xorg/2005-July/008751.html](http://lists.freedesktop.org/pipermail/xorg/2005-July/008751.html))
Try this patch. The synaptics driver comes with deprecated headers.


--- orig-synaptics-0.14.2/Xincludes/usr/X11R6/include/X11/Xfuncproto.h
2005-03-29 00:29:50.000000000 +0800 
+++ synaptics-0.14.2/Xincludes/usr/X11R6/include/X11/Xfuncproto.h
 2005-03-29 00:29:50.000000000 +0800 
@@ -69,4 +69,12 @@ 
 #endif 
 #endif /* _XFUNCPROTOBEGIN */ 
  
+#if defined(__GNUC__) && (__GNUC__ >= 4) 
+# define _X_SENTINEL(x) __attribute__ ((__sentinel__(x))) 
+# define _X_ATTRIBUTE_PRINTF(x,y) __attribute__((__format__(__printf__,x,y))) 
+#else 
+# define _X_SENTINEL(x) 
+# define _X_ATTRIBUTE_PRINTF(x,y) 
+#endif /* GNUC >= 4 */ 
+ 
 #endif /* _XFUNCPROTO_H_ */

Adding all the lines above with pluses to that file (I'm sure there's a utility that does this, but I couldn't remember what it was) got it to compile correctly for me. I've finally turned off touchpad tapping in breezy and I'm very happy now.

---

### Post by bryan986 on 2005-10-17
actually, if you install libxext-dev, it depends on the other two in one way or another...

the patch command can be used to apply that to the source

---

### Post by RSX311 on 2005-10-18
[QUOTE=tetsuo29]The packages that need to be installed are:
- x-dev
- libx11-dev
- libxext-dev

[/QUOTE]


I did apt-get to all those and it installed fine, but I still can't type make.  It still says command not found?

---

### Post by GoodPanos on 2005-10-18
Where on earth does all that code have to go???  Which file needs to be edited with that code???  Is this code an addition to existing code or the complete header should look like that?

**RSX311**, make sure you have the "make" package installed.  Go to System\Administration\Synaptic Package Manager.  Then look for package "make" check it and then install it.

Or you can simply type at the terminal *sudo apt-get make*.

Hope that helps.

---

### Post by bryan986 on 2005-10-18
If you are missing make, you should just get build-essential, that will install everything needed for buliding

---

### Post by RSX311 on 2005-10-18
thanks guys, that worked! now to get my damn touchpad to work :(

---

### Post by jrronimo on 2005-10-18
Gateway Solo 5300 with a Synaptics touchpad.

I have been having the 'hyper mouse' issue since 4.10. The sensitivity setting in system -> preferences -> mouse has never really had any effect.

I switched the first mouse driver from "mouse" to "synaptics" at the suggestion of some other post. The mouse responded MUCH better, except that sometimes just mousing around in Opera would cause it to randomly go back like a half-dozen webpages.

So I've tried switching it back and now there seems to be no effect.

I've tried the command listed previously in here (sudo sh blah blah blah) but I am not sure if it has worked.

Once one changes the sensitivity of their mouse in sytem -> preferences -> mouse, how does one enable these changes? Is a full reboot required in order to change the sensitivity of the mouse?

---

### Post by DrMoxie on 2005-10-18
[QUOTE=Pausanias]Don't be such a pessimist. This will get drag-and-drop working:

```

sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe"

```

Then reboot.[/QUOTE]

Thanks to everyone here for helping out on this issue I finally got the touchpad working with the above code, though in a round about way--it wasn't as simple as copy, paste, reboot.  I rolled the driver back in Synaptic where, not to my surprise, it was still screwy even after a dpkg-reconfigure for xserver.  I upgraded it, rebooted again, did another dpkg-reconfigure, then copy-paste-reboot and it is working.  

I'm sure that the rollback-upgrade-dpkg dance was overkill but after all that the above code worked.  Not sure why but I have my touchpad back.  Thanks! \\:D/

---

### Post by GoodPanos on 2005-10-19
Any suggestions on getting the vertical scrolling working?

---

### Post by zelah on 2005-10-26
[QUOTE=GoodPanos]Any suggestions on getting the vertical scrolling working?[/QUOTE]
how about to not work? thats what i'm interested in

when i'm typing in gaim and the cursor is on the window near the tabs, the lightest graze makes it switch who i'm talking to, and i dont like that

if i move it of to whatever page is behind gaim, then that just scrolls up and down obnoxiously

i remember seeing something about how to disable it, but i dont want to go blindly "false"ing things in my xorg.conf

---

### Post by Sunnz on 2005-10-28
How do I get vertical scrolling to work?

---

### Post by wharfratjoe on 2005-10-28
Just a fyi, the nic, touchpad and video drivers from knoppix 3.9 live cd works on my hp zv6000 laptop. I will post how ndiswrapper works out for the wireless with knoppix. It works fine using this fix ( [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683) ) when I had Ubuntu installed on the laptop.

 If the drivers from that cd can be ported over to Ubuntu maybe some hardware issues with what I was having with ATI/Radeon (no accel option enabled) and the touchpad will work with Ubuntu. I do not know how to port over drivers from one distro to another(yet) and if it is even possible to do.

I tried Ubuntu on this laptop and the fixes posted here for the touchpad but nothing worked. It will however, plug and play a usb mouse with no problem.

just a fyi, I have been trying multiple distro's and had all of them dual booting with XP Pro with no problems other than what I mentioned above when logging into a Linux OS

Hardware is the following:
HPZV6000 (US)
AMD 64 Athlon 3200+ Processor
512MB (2x 256MB) DDR SDRAM
80gig 5400rpm HD
8x DVD+/-RW CD-RW Combo Drive
15.4 WXGA Widescreen TFT (1280 x 800) Display
128M ATI Radeon xpress200m w/ HyperMemory (dedicated)
Integrated 54g Broadcom Wireless NIC
Integrated 10/100 nic
16bit  SoundBlaster Pro
Synaptics Touchpad

Peace,
Joe

---

### Post by quasi-aussie on 2005-11-03
Considering all the doom&gloom preached in this thread, you would be well advised to mosey on over to the much more upbeat thread found [here]("http://ubuntuforums.org/showthread.php?t=78904") for a description of how to solve the ALPS touchpad woes for a number of notebooks with this same problem. The guy starting the thread has a Sony, another guy has a DELL and I have an HP Pavilion dv4000, and we're all happy campers now.
The thread goes on for quite a while, but the solution (for me) was contained in the very first post.
I included one other option (Option "GuestMouseOff" "0") in my xorg.config to improve dragging, but the rest works sweet as...

---

### Post by Sunnz on 2005-11-03
Really? I too have a dv4000 but haven't got any luck yet... may I see your xorg.conf?

---

