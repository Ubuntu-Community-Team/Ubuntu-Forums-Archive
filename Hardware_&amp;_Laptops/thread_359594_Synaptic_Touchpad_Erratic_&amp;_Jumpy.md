---
title: "Synaptic Touchpad Erratic &amp; Jumpy"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by mlaverdiere on 2007-02-12
Hi,

Since a couple of weeks, my synaptic touchpad behaves strangely on my Compaq Presario V2610CA with (K)Ubuntu Edgy.  This is an intermittent problem:  things are going well for a while, then the mouse cursor becomes erratic and jumpy.

I've tried every solution that I've found on the web:

- Playing with my synaptic configuration xorg.conf file, in order to reduce the sensitivity, turning off the tap to click option, etc.
- Turning off powernowd and ACPI, since it appears that they may affect the touchpad functionning, etc.
- Other small tweaks that gave nothing goog...

Since everyhting was working well up to 2 or 3 weeks ago and that the problem started out of the blue, I thought at some point taht this may be a hardware problem.  But the thing is that the Touchpad is working well with WinXP.

For me, it could make sense if the cause wase related to a bad acpi/powernowd setup, since the problem is intermitent and could be caused by some kind of CPU frequency adjusting....  But even if I turn powernowd/acpi off and rmmod the associated modules, the problem still occurs.

Anyway, here's the relevant part of my xorg.conf file:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig" "on"
EndSection


Any idea someone?

Thanks for your help.

---

### Post by Tedd on 2007-02-12
You could always get a wireless laptop mouse if all else fails- I have a nice one with a USB reciever that I've had for six months and haven't replaced the batteries. $19 ftw.

Although that's just me- I abhor using the touchpad. Maybe there's a certain Linux driver or module for touchpads on the Ubuntu repos?

---

### Post by Trance Gemini on 2007-02-12
Well, as for me I have jumps only when I reboot and touch the touchpad for the first time. Then all other touches works fine. Do you have the same?

---

### Post by mlaverdiere on 2007-02-12
No, it's not just upon reboot.  It's unpredictibable...

---

### Post by vanlinx on 2007-02-12
hey, 

this might not be related, but since friday I have installed Debian, Edgy, Knoppix and finally Hoary 5.04 (oldschool) which seems rock solid, like no stupid jumpy mouse, touchpad things. Hoary also automatically detects wireless card AND that damn annoying 340M IGP ATI card. So Glxgears works not too bad, getting about 280-300fps. Hence can install 3ddesktop, which looks good ^__^. but i know beryl and all those are better, not too sure if they run on hoary tho...

---

### Post by danboy on 2007-04-16
did anyone ever find a solution for this?it's killing me to not have a working touchpad, and i'm having crazy keyboard issues as well.

---

### Post by Cartwheels4amile on 2007-04-23
You're not alone. I have Compaq Presario v5306us, and the touchpad is jumpy at random intervals as well. It seems more stable when I'm only running off battery power, but this could just be me. I'm running Feisty, and I was wondering if anybody had a fix for this.

---

### Post by stenka on 2007-04-24
Same here on a Sony laptop. Every new version of Ubuntu brings a new generation of very anoying bugs...

---

### Post by dsiddens on 2007-04-30
Just did the upgrade from Drapper to Fiesty and am back with erratic synaptics touchpad.

After a reboot it will drag scroll, double click... but after a period of use, usually within 3 hours it looses its drag scroll and double click.  Also the cursor can jump on the screen.

---

### Post by ccolella on 2007-04-30
Same here. I have the same Compaq laptop Cartwheels mentioned, with an ATI shared-memory graphics card, and a Synaptics touchpad. The mouse is simply unusable in its current state. I'm using Fiesty, but maybe I'll switch to Hoary until this is resolved. However, I'm sure it's not a native Ubuntu problem. I have installed every new distro I could find, and they all have the same problem. (Ubuntu, Mandriva, Sabayon, Linux Mint) I'd like to know if older distros don't have this problem. I know it's not my hardware, because Windows works just fine.

---

### Post by bakermiller on 2007-04-30
same here. 
Feisty. 
on an acer laptop.
synaptic touchpad freezes.
Keyboard too (microsoft USB 2000v1.0). 
luckily, i also have a usb mouse :P
It does not always freeze, mostly when i'm running on the battery.
(don't know if it's related or just coincidence).

---

### Post by BrokenPoet on 2007-06-05
I'm seeing the same symptoms as the original poster: Erratic, 'jumpy' mouse movements when the finger is removed from the pad and then replaced.  Quite frustrating when attempting to navigate through pulldown menus!

Toshiba Satellite 5205-S503
Synaptics Wheelpad 06cb:0008
Feisty 7.04

---

### Post by treggmo on 2007-06-06
Hey, I had an erratic Touchpad that was testing me so I googled and found 3 apps and ended up with gsynaptics (not qsynaptics or ksynaptics, they didn't work the way I wanted). gsynaptics added itself to the Startup Programs list and the GUI is at System > Preferences > Touchpad. Install it, configure and............... ..............relax:D

It's in the repositories. I installed it with aptitude.
I'm running Feisty on an Asus A7J

Edit: Forgot the link:

[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

---

### Post by masked_marsoe on 2007-06-06
I have had the same problem on an NEC Versa A2100.

But only with Feisty, Edgy works _fine_.

Im just about to try the thing above.

---

### Post by masked_marsoe on 2007-06-06
The keyboard lag hasn't been fixed, but the touchpad is better.

---

### Post by BrokenPoet on 2007-06-07
I had tried installing each of the three apps (including 'gsynaptics') to no avail.  Attempting to start 'gsynaptics'  results in the following error:

[COLOR="MediumTurquoise"]"GSynaptics couldn't initialize.  You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"[/COLOR]

   I have added the aforementioned 'SHMConfig' line to xorg.conf as follows, with no change in the result:

[COLOR="MediumTurquoise"]Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection[/COLOR]

     Has anyone else run into this?  (Or have I incorrectly added the SHMConfig line?)

---

### Post by nardis_Miles1 on 2007-06-09
Just curious about the specifics of your laptop. Make, model?

---

### Post by BrokenPoet on 2007-06-10
nardis-

Toshiba Satellite 5205-S503
Pentium4m 1.7Ghz, 512Mb RAM
Synaptics Wheelpad 06cb:0008
Feisty 7.04

---

### Post by kbsuperstar on 2007-06-16
While this is not a complete fix to the problem that synaptics is plaguing us with,  I've found some tweaks that work rather well.

Just open up xorg.conf and enter the following under <b>Section</b> "Input Device" > Identifier "Synaptics Touchpad"

```
Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option 		"Device" 		"/dev/psaux"
	Option 		"Protocol" 		"auto-dev"
	Option		"LeftEdge"		"1900"
	Option		"RightEdge"		"5400"
	Option 		"TopEdge"		"1900"
	Option	   	"BottomEdge"		"4000"
	Option 		"FingerLow" 		"25"
	Option 		"FingerHigh"		"30"
	Option 		"MaxTapTime" 		"180"
	Option 		"MaxTapMove"		"220"
	Option 		"VertScrollDelta" 	"100"
	Option 		"MinSpeed"		"0.02"
	Option 		"MaxSpeed"		"0.18"
	Option 		"AccelFactor" 		"0.0010"
	Option 		"SHMConfig"		"on"
	# Option 	"Repeater"		"/dev/ps2mouse"
```

Also install <b>gsynaptics</b> from Synaptic and reboot.

I would recommend disabling vertical and horizontal scrolling seeing as how it causes random window changes and it screws up beryl while on the desktop.

Good luck everyone!

P.S. -- I don't think this really matters, but I'm using Linux Mint if ya'll want to know. It's built off Ubuntu and it uses the same repositories. I love it  :D

---

### Post by BrokenPoet on 2007-06-16
KB-
   Thanks for the direction, but unfortunately no change in the problem.  Even after changing the 'True' to 'on', I am a) unable to start 'gsynaptics' with the same error quoted above and b) still exhibit the jumpy cursor.

   I'm not sure which of these irritates me more, I feel like playing,  "I'm squishing your head" with that darn gsynaptics error message.  I guess pressing the red X will have to suffice, if I can track to it.

   Any other thoughts?

---

### Post by kbsuperstar on 2007-06-17
Yeah, I've gotten gsynaptics to work, but unfortunately it doesn't help much. My mouse is still rather finnicky, and it is quite irritating even after disabling scrolling.

Hopefully someone finds a better tweak or perhaps a total solution :) That'd be nice

---

### Post by groovomata on 2007-06-20
I've had similar problems with my compaq v5000 laptop with the ati Xpress 200m video card. I discovered that if I blacklisted BCM43xx and used ndiswrapper instead it helped, also I stopped using beryl which helped a lot. It's still not perfect but it is much better. Here is the thread that I started:
[http://ubuntuforums.org/showthread.php?t=419675](http://ubuntuforums.org/showthread.php?t=419675)

---

### Post by defenestratos on 2007-07-07
I have  a Benq Joybook R23 and I have the same problem. The Logitech USB mouse quivers and shakes, and while I type it sometimes clicks randomly. There it just did it. I am sure it has something to do with the synaptics touch pad because when I unplug the mouse it still happens. Doesn't happen in Windows.

---

### Post by Sefianix on 2007-07-12
> **groovomata said:**
> I've had similar problems with my compaq v5000 laptop with the ati Xpress 200m video card. I discovered that if I blacklisted BCM43xx and used ndiswrapper instead it helped, also I stopped using beryl which helped a lot. It's still not perfect but it is much better. Here is the thread that I started:
[http://ubuntuforums.org/showthread.php?t=419675](http://ubuntuforums.org/showthread.php?t=419675)

Groovomata, I have the same problem and the same laptop, v5000.  The touchpad is driving me crazy.  [saw your post; thanks for the instructions]

Thanks!

---

### Post by shabri on 2007-08-04
Bump!!

I have this problem, gsynaptics doesn't seem to make a difference.  

Be nice if someone could help!

---

### Post by TravMan63 on 2007-08-08
My touchpad (Dell C840 Latitude) isn't really quirky - but it's WAY too touchy.

Also have Elive dual boot same machine - and the pad is WAY S L O W....

somewhere in between would be nice..

will give gsynaptics a try...

TM

---

### Post by Cartwheels4amile on 2007-09-03
Damn, this problem still has no solution? I'm stuck using Vista because of this. Hopefully Gutsy will fix the issue. =/

---

### Post by k1773r37f on 2007-10-11
Good news.  I found a solution to our synaptics problem.  add i8042.nomux=1 to the kernel line in /boot/grub/menu.lst

Bad news that shifts the problem to the keybaord.  Causing it to lockup continuosly repeating the key pressed at the time of lockup.  After obligatory reboot, no clues in /var/logmessages.

Choose your evil wisely.

---

### Post by riviera84 on 2007-10-21
Yes, ony my HP Pavilion dv8903us laptop. Same exact error. That's why GSynaptics does not work. My key board has some sticking issues as well, but not much better in windows.

---

### Post by Pierre Hanser on 2007-11-18
hello
I had the same problem on an acer1520 with ubuntu 7.10:
mouse erratic and freezing, unfreeze with keyboard use

the solution for me seems to use package synaptics-0.14.6 which
I was already using on my previous Mandrake 2005 distro

make
make install
in xorg.conf, module section add Load "synaptics"

this does not avoid touchpad resynchronisation problems, but

 - they are very short
 - the mouse does not jump everywhere

It's like day and nigth...

---

### Post by ZeroHimself on 2008-03-26
Same "jump" problem with my touchpad, running gutsy(7.10)

i'll wait for it to happen again, and then i will try gsynaptics, and let you guys know
BTW my laptop volume control wheel seems to get erratic at the same time as the mouse....
wierd

toshiba satellite x205-s9359

---

### Post by gantayet on 2008-04-03
Try 'syndaemon' command from the console

syndaemon -d -t

This should sort out your problem. To know more about it use 'man syndaemon'

HTH

---

### Post by billtron on 2008-04-26
Has anyone figured out what's happening with this?

My touchpad also acts erratically, but it has started happening in Windows as well.  The blue mouse pointer button on my Latitude D630 also acts up sometimes, and earlier this morning my USB mouse started freaking out as well.

I think it gets progressively worse the longer the computer is on.  It's always best right after I start up.

---

### Post by billtron on 2008-04-26
So I realized that my touchpad is erratic when I am running on battery power, which leads me to believe it's a hardware problem.  Any ideas?

---

### Post by mlaverdiere on 2008-04-29
I'm the poster of the first message of this thread and I just want to let you know the conclusion of my experience with this problem:  It was a hardware problem!  My laptop was still under warranty so the touchpad has been replaced and everything works well now.

I would suggest that if an erratic synaptic touchpad problem can't be solved by adjusting configuration in xorg.conf (through gui config tools like gsynaptics for Gnome/XFCE or ksynaptics for KDE), there's good chance that it is a hardware problem...

Just my 2 cents!

---

