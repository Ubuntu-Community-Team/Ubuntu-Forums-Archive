---
title: "Can't Boot After Upgrading To 2.6.31"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by angel120 on 2009-07-07
EDIT: Take a look at post #84 to see how I was able to set up my touch and stylus for this laptop

I have an HP TouchSmart TX2 (N-Trig screen, 4GB RAM, AMD64 @ 2.1GHz, Radeon HD3200, etc), and I tried upgrading my kernel from 2.6.28.
I found instructions here ([http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)), and I downloaded the program he linked to.  Ran the program, and now I can't boot into any of my kernels!  I can still get into recovery mode, but whenever I try to boot, I see the following:

[IMG]http://i77.photobucket.com/albums/j43/doublebass120/ubuntu%20kernel%20problem/0707090204a.jpg[/IMG]
[IMG]http://i77.photobucket.com/albums/j43/doublebass120/ubuntu%20kernel%20problem/0707090205.jpg[/IMG]
[IMG]http://i77.photobucket.com/albums/j43/doublebass120/ubuntu%20kernel%20problem/0707090205a.jpg[/IMG]

Just as a reference, here's my GRUB menu:
[IMG]http://i77.photobucket.com/albums/j43/doublebass120/ubuntu%20kernel%20problem/0707090204.jpg[/IMG]

Can this problem be fixed without having to do a reformat?  I really don't want to because I have school work that I most likely don't have backups of..

In any event, thanks in advance for any and all help.
-Angel.

---

### Post by Mark Phelps on 2009-07-07
Have you tried selecting the older kernel? If the standard selection doesn't work, you could also try the recovery mode.

Granted, these won't fix the problem with the new kernel but at least you'll have a working machine back.

---

### Post by angel120 on 2009-07-07
Yeah, I've tried all selections, the only thing that works is if I boot into recovery mode.  I can only get the command line, though.  If I select "Resume Normal Boot," the same thing happens.  I tried uninstalling and reinstalling fglrx, but that doesn't help at all..  What sucks is that I followed the same procedure for my desktop!  Good thing I dual-boot...

---

### Post by darco on 2009-07-07
You could always boot from the Live CD and recover what you need at least. 
The Live Cd may be your ticket to fix this issue but I dont know....
I just upgraded to .30 but didnt compile my kernel and its running great.

good luck
darco

---

### Post by angel120 on 2009-07-07
I didn't know the LiveCD was capable of doing that..  Thanks!
How did you upgrade your kernel?  I've tried 2 different methods, and the same exact thing happened (but with the first method, I was still able to use my old kernels)..
My first method was to download the headers and image .deb packages and install them like that.  But since my old kernel(s) worked, I was able to switch to the older ones and simply uninstall 2.6.30..

---

### Post by darco on 2009-07-07
the quick and easy way!

[http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/)

darco

---

### Post by angel120 on 2009-07-07
Yup, those were the instructions I followed the first time around.. No such luck for me!

I can't be the only person here that has experienced a problem upgrading a kernel....

---

### Post by darco on 2009-07-07
isnt .31 rc?..I wouldnt touch those....

darco

---

### Post by angel120 on 2009-07-07
Thanks for catching that typo!  I misread the number, it's 2.6.30.1, not 2.6.31.  You can see my GRUB in the last pic of the first post.

---

### Post by angel120 on 2009-07-07
Bump..

Fixed the 2nd pic of the 1st post..  Didn't realize I used the same pic twice.

---

### Post by synace on 2009-07-09
i see that result when i was trying to get my touch/pen working on 9.04.

if i restore the original (fglrx) or failsafe (vesa) xorg.conf, i'm good to go.

 - boot into recovery mode
 - drop to a root shell w/ networking
 - fix /etc/X11/xorg.conf (or copy /etc/X11/xorg.conf.failsafe to /etc/X11/xorg.conf)

i can boot normally again. 

note, whenever this happens, i lose keyboard input too it seems.

---

### Post by Favux on 2009-07-09
Hi synace,

You don't need to do a kernel upgrade in Jaunty to get the stylus and pen working for your n-trig digitizer anymore.  This link will take you to a xorg.conf and a link to Ayuthia's deb.s and instructions.  See appenidix 2 at the bottom:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

---

### Post by synace on 2009-07-09
side note, to get rid of the old kernel (from a root recovery shell):

uninstall the extra kernel

dpkg --purge ...headers
dpkg --purge ...headers-generic
dpkg --purge ...image...

apt-get install --reinstall ...headers
apt-get install --reinstall ...headers-generic
apt-get install --reinstall ...image...

your current kernel's parts (headers, headers-generic & image)

you should be able to boot back to where your machine was before you added the extra kernel

---

### Post by synace on 2009-07-09
> **Favux said:**
> Hi synace,

You don't need to do a kernel upgrade in Jaunty to get the stylus and pen working for your n-trig digitizer anymore.  This link will take you to a xorg.conf and a link to Ayuthia's deb.s and instructions.  See appenidix 2 at the bottom:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

checking it out.. i didn't upgrade, just wanted to get the stylus & right click working (right now the button is middle-click). 

i'll try those patched kernel files.

edit:
i'm actually on 2.6.28-13.45, those are 2.6.28-13.44

i used the xorg.conf in the bzip package in his post.

got a warning about downgrading.. rebooting & trying

i ended up w/ the same thing seen on page 1 here.

trying xorg.conf adjustments. if that doesn't work, i'll reninstall .45.

that worked.. ok.. i'm on Ayuthia's patched kernel, but his xorg.conf doesn't work for me. fglrx does work for me.

touch 'IS' working (it's no-longer going to the top-left corner, X11 registers something). although, it's not responsive or accurate and sporadic. maybe have to adjust wacom sensitivity? if i use 3 fingers, it works, 1 finger, no go.

pen works still, though, button is still middle click.

my xorg.conf:

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Trackpad"
        InputDevice     "stylus"
# I've commented out the eraser because it either doesn't exist or doesn't work
#        InputDevice    "eraser"  # "SendCoreEvents"
        InputDevice     "touch"
EndSection                                 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Load	"dri"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Section "InputDevice"
	Identifier  "Trackpad"
	Driver      "synaptics"
	Option	"Device" "/dev/input/by-path/platform-i8042-serio-1-event-mouse"
EndSection

Section "InputDevice"
	Driver "wacom"
        Option "Mode" "Absolute"
        Identifier "touch"
	Option "Touch" "on"
        Option "Type" "touch"
 	Option "ForceDevice" "ISDV4"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#        Option "USB" "on"
	Option "TopX" "0"
	Option "TopY" "0"
	Option "BottomX" "9600"
	Option "BottomY" "7200"
	Option "DebugLevel" "8"
# 	Option "Button1" "1"
# 	Option "Button10" "1"
EndSection

Section "InputDevice"
        Driver "wacom"
        Identifier "stylus"
        Option "Mode" "Absolute"
        Option "Type" "stylus"
 	Option "ForceDevice" "ISDV4"
 	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
 	Option "TPCButton" "on"
        Option "USB" "on"
        Option "Button2" "3"
#        Option "Button3" "core key alt F2"
EndSection

```

---

### Post by Favux on 2009-07-09
Hi synace,

Use the xorg.conf attached to the bottom of the HOW TO that appendix 2 is on, linked above.

Ayuthia says swiping a couple fingers across the screen gets touch back for him.

See, starting with about post #12, more info. here:  [http://ubuntuforums.org/showthread.php?t=1162477&page=2](http://ubuntuforums.org/showthread.php?t=1162477&page=2)

---

### Post by synace on 2009-07-09
using that one gives me a screen similar to post 1 in this thread, after which i have to shutdown (power button), boot into recovery, fix xorg.conf and start over.

---

### Post by Favux on 2009-07-09
Hi synace,

Looks like that's due to the way you have "fglrx" setup.  Just swap the wacom entries for stylus and touch in the order they are in for the ones you have.  Also include the wacom "ServerLayout" entries.  Ayuthia mentioned he had to reinstall ATI proprietary after substituting in his patched kernel.

---

### Post by synace on 2009-07-09
so, keep my xorg, make stylus first, touch 2nd?
in the server layout or their individual sections?

---

### Post by Favux on 2009-07-09
In their sections and in serverlayout just like it is in the TX2z xorg.  Leave the rest the way you have it.  Or I could do it if you need me to.

---

### Post by Favux on 2009-07-09
Hi synace,

It should look something like this.

---

### Post by synace on 2009-07-09
i setup SSH so i can keep retrying now ;)

---

### Post by synace on 2009-07-09
tried yours. touch is much more responsive now & right-mouse click works on the pen THANKS!!! =D>=D>.

i added my final file here for reference. works for me.

 - HP Tx2z
 - Ubuntu 9.04 + all updates as of 2009/07/09
 - flgrx proprietary drivers
 - patched (downgraded minor version) kernel ([http://linuxfans.betaserver.org/packages/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb](http://linuxfans.betaserver.org/packages/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb)  [http://linuxfans.betaserver.org/packages/linux-headers-2.6.28-13-generic_2.6.28-13.44_amd64.deb](http://linuxfans.betaserver.org/packages/linux-headers-2.6.28-13-generic_2.6.28-13.44_amd64.deb))
 - supplied xorg.conf file
```

# HP tx2z N-trig touch & digitizer pen as right-click
# Uses patched kernel from Ayuthia at ubuntuforums.org:
#    http://linuxfans.betaserver.org/packages/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb
#    http://linuxfans.betaserver.org/packages/linux-headers-2.6.28-13-generic_2.6.28-13.44_amd64.deb
# NOTE: order of items is significant. do not re-arrange.

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"Button2"	"3"	# make stylus button R mouse click
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option		"Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option		"Type"		"touch"
	Option		"USB"		"on"
	Option		"Touch"		"on"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"9600"
	Option		"BottomY"	"7200"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load		"glx"
	Load		"dri"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection

```

---

### Post by synace on 2009-07-09
i notice that palm still activates touch in presence of the digitizer, though, the digitize seems to take precedent as the preferred position of the cursor. is this the whole driver issue that was discussed (the coordinates are sent to the wacom driver before the input device)?

what were the results of your investigations into having stylus input activity disable the touch input activity?

---

### Post by synace on 2009-07-09
i have to roll for now. tomorrow i'll try to tackle rotation.. (broken rotation w/ fglrx + compiz? :()

---

### Post by Favux on 2009-07-09
Hi synace,

You are welcome.

Order may or may not apply only to stylus then touch.  May be more due to which section has coordinates.  "ServerLayout" generally should be at the end, although the "Module" section could probably come after.

Right, problem may be due to N-trig firmware sending before device identified.

Looks like you're caught up to where we are.

So do we need Rafi or who ever to reorder, identifying device (stylus, touch) first.

Only other options are the ones listed.  Try 0.8.3-x wacom.ko or mess with the parameters.

So if you want to investigate and find out something maybe post to the other thread.

Edit:  Yes, rotation doesn't work with Compiz and "fglrx", that's why I have the Compiz_off_Rotation script above the TX2z & XT xorg.conf.  Keyboard stops working or other bizarre stuff.  Rotation is fine without Compiz as long as you've run the aticonfig command.

---

### Post by synace on 2009-07-09
thanks for your help. i was reading somewhere about the ability to adjust the sensitivity of the 'touch' driver. right now, i really have to nail on it, with something fine-point like a fingernail. touching does not work so much as tapping.

---

### Post by Favux on 2009-07-09
Hi synace,

Right:
```
Option "Capacity" "number"
```
from LWP HOWTO here:  [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)  It seems like it should work for N-trig, but Nimless said it wasn't.

---

### Post by synace on 2009-07-10
no change between the two. (-1 vs 5)

i find that:

one finger, tapping = 50% responsive

two fingers (index middle) together, 70% responsive, cursor centered between

one finger, tapping and sliding about 1cm then releasing (sort of a radial tap) 90% responsive, 50% dragging.

:confused:

i tried playing with the following settings (in both the stylus & touch input devices):

#       Option          "Threshold"     "15" # no effect from 5 to 25 (not sure of possible range)
#       Option          "Capacity" "3" # no effect from -1 to 5

no noticeable difference was made

---

### Post by synace on 2009-07-10
Favux,

I've got xrandr -o normal & xrandr -o right working w/ fglrx & metacity.

I've tried to determine if there is a way to support auto-rotation based on input from the button triggered when you physically rotate the tablet, and/or the panel buttons (rotate, checkmark, gear), but the only information I can find is a patch for kernel 2.6.30. I'm locked to the patched 2.6.28-13.44 kernel at this time. Do I have any chance of seeing input from those panel buttons or the physical rotation indicator?

also, i've got wacomrotate, but i'm not sure i understand it's purpose. xrandr -o right seems that everything works. (ok.. nvm, maybe it's because of wacomrotate.. it's running ;))

i've bound Shift+Control+Alt+R to the rotate script i found & modified:

/usr/local/bin/trotate
```

#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 
rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 
case "$rotation" in 
    normal) 
    # rotate to the left 
    # start metacity
    metacity --replace &
    xrandr -o left 
    ;; 

    left) 
    # rotate to inverted 
    xrandr -o inverted 
    ;; 

    inverted) 
    # rotate to the right 
    xrandr -o right 
    ;; 

    right) 
    # rotate to normal 
    xrandr -o normal 
    # start compiz
    compiz --replace &
    ;; 
esac

```

---

### Post by synace on 2009-07-10
since a fresh reboot touch works flawlessly now, light touches = input! investigating...


as soon as the digitizer first interacts with the screen my touch input goes back to spotty.

note, while trying to highlight text in the terminal, the cursor bounces around to a few positions on the screen. open terminal, highlight some text.. watch. bounce every 2/3 seconds. i've seen 3-5 consistent positions so far.

after bringing in the digitizer pen, the touch responsiveness goes back to about 50% and the cursor bouncing is still present. so, the bouncing has nothing to do w/ touch or digitizer, it's present in both.

the touch responsiveness goes down to about 50% once the digitizer is first used.

thoughts?

---

### Post by Favux on 2009-07-10
Hi synace,

Post #28:  Not too surprising Threshold did nothing, I think it's for stylus (maybe eraser).  But worth trying everything for sure.  Section 5.1 on the LWP HOWTO can have more complete definitions.  Capacity is disappointing.  I think that suggests what we suspected, N-trig isn't too well integrated with the linuxwacom drivers yet.  Plenty more parameters to play with.

Post #29:  TX2000 and TX2500 only have had 2 out of 4 bezel buttons working.  Xorg seems to love changing button mapping with each Xserver version so going to Intrepid broke those 2 buttons.  What we did was stop the hotkey-setup daemon, broke the sym links, and restarted it.  That got the 2 bezel buttons back in Intrepid.  That's the key code addendum on the Rotation HOW TO.

HP changed the bezel buttons on the TX2z so the situation is even worse.  If xev didn't give a keycode you were out of luck.  Because I've seen other laptops map their buttons through their kernel module, my guess is the signal is going to HP-WMI, but Matthew Garrett hasn't set it up to deal with buttons.  Which is weird since he has a TX2500.

You could try lshal and see if an "unknown button(s)" is present.  Or use the HAL gui front end Device Manager.

On the swivel hinge my understanding is that you are suppose to apply Matthew's patch to the 2.6.30 module and then replace the 2.6.28 module with it.  Not sure what the problem is, maybe with MisteR2's .fdi.  If I understood Ayuthia correctly there is a button "press" event from the hinge, but no "release".  So apparently nothing happens.  So may be the .fdi or it may be there needs to be a laptop specifie "quirk" added upstream to the .fdi where all the brand specific configuration .fdi's are.

Run either script or wacomrotate, not both.  With wacomrotate the command for the launcher or the keybinding is (xrandr -q | grep -q '+\w* (' && xrandr -o right || xrandr -o normal).  The sleep was just to give Compiz enough time to shut down.  I didn't want breakage  from rotation too soon.  I wonder if Compiz would work in inverted?

Post #30:  So maybe the packets being sent before device identified thing.  If that got "corrected" would everything start working?

---

### Post by synace on 2009-07-10
> **Favux said:**
> Hi synace,
Post #29:  TX2000 and TX2500 only have had 2 out of 4 bezel buttons working.  Xorg seems to love changing button mapping with each Xserver version so going to Intrepid broke those 2 buttons.  What we did was stop the hotkey-setup daemon, broke the sym links, and restarted it.  That got the 2 bezel buttons back in Intrepid.  That's the key code addendum on the Rotation HOW TO.

HP changed the bezel buttons on the TX2z so the situation is even worse.  If xev didn't give a keycode you were out of luck.  Because I've seen 
other laptops map their buttons through their kernel module, my guess is the signal is going to HP-WMI, but Matthew Garrett hasn't set it up to deal with buttons.  Which is weird since he has a TX2500.

I applied the startup change to hotkeys (the only change i saw was to have it start in level 1, if i'm reading it correctly). xev does not report anything for the 3 bezel buttons. i'd be willing to test. do you know what URL he maintains the HP-WMI at? i'll google-fu it.

> **Favux said:**
> 
You could try lshal and see if an "unknown button(s)" is present.  Or use the HAL gui front end Device Manager.

On the swivel hinge my understanding is that you are suppose to apply Matthew's patch to the 2.6.30 module and then replace the 2.6.28 module with it.  Not sure what the problem is, maybe with MisteR2's .fdi.  If I understood Ayuthia correctly there is a button "press" event from the hinge, but no "release".  So apparently nothing happens.  So may be the .fdi or it may be there needs to be a laptop specifie "quirk" added upstream to the .fdi where all the brand specific configuration .fdi's are.

so, even with the kernel patch it's only half working? i'll see if lshal shows anything.

> **Favux said:**
> 
Run either script or wacomrotate, not both.  With wacomrotate the command for the launcher or the keybinding is (xrandr -q | grep -q '+\w* (' && xrandr -o right || xrandr -o normal).  The sleep was just to give Compiz enough time to shut down.  I didn't want breakage  from rotation too soon.  I wonder if Compiz would work in inverted?

i find that they were working well together, though, i've removed the wacomrotate daemon and added the xsetwacom calls back:
```

#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 
rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 
case "$rotation" in 
    normal) 
    # rotate to the left 
    # start metacity
    metacity --replace &
    xrandr -o left
    xsetwacom set stylus rotate CCW
    xsetwacom set touch rotate CCW
    ;; 

    left) 
    # rotate to inverted 
    xrandr -o inverted 
    xsetwacom set stylus rotate HALF
    xsetwacom set touch rotate HALF
    ;; 

    inverted) 
    # rotate to the right 
    xrandr -o right
    xsetwacom set stylus rotate CW
    xsetwacom set touch rotate CW
    ;; 

    right) 
    # rotate to normal 
    xrandr -o normal
    xsetwacom set stylus rotate NONE
    xsetwacom set touch rotate NONE
    # start compiz
    compiz --replace &
    ;; 
esac

```

> **Favux said:**
> 
Post #30:  So maybe the packets being sent before device identified thing.  If that got "corrected" would everything start working?
i think that could be utilized to 'kill' touch when the digitizer is near (palm/hand ignore). then, when the digitizer is gone for a timeout, listen for a distinct double touch to re-activate? hrm.. have to talk to the driver dev. i'm willing to test! ;)

---

### Post by Favux on 2009-07-10
Hi synace,

I may have the url for HP-WMI, I'll have to look around.  I think I've seen him posting on the kernel.org list and his blog.

Sorry I misunderstood what you were saying with wacomrotate.  What you were doing is fine.  Wacomrotate just has the xsetwacom calls built in.  Tom Jaeger feels that's the way Xserver should be set up to begin with.  By the way check out his EasyStroke program.

I don't have a contact for Rafi Rubin.  Just his XT site with the patches and I see him posting on the LWP dev-list.

Edit:  A little more info. from Nimless on post #34:  [http://ubuntuforums.org/showthread.php?t=1162477&page=4](http://ubuntuforums.org/showthread.php?t=1162477&page=4)

---

### Post by synace on 2009-07-10
reading about fglrx + compiz + xrandr..

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/132065](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/132065)

ahh.  i see:
> **Nimless said:**
> 
Also the problem of the "finger taps" persist on both firmware after using stylus, but apparently as Ayuthia said sliding two fingers on the screen solves the problem o_O

On kernel 2.6.31-rc1 from the ubuntu kernel ppa the problem is persistent.

yeah, using two fingers provides no restoration to the 100% awesomeness that i first get w/ boot & not using stylus.



should i try the ati or radeon driver(s)?

[http://ubuntuforums.org/showpost.php?p=4237027&postcount=43](http://ubuntuforums.org/showpost.php?p=4237027&postcount=43)

synace@synacetablet:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics 
OpenGL version string: 2.1.8575

---

### Post by Favux on 2009-07-10
Yep, good luck with that one.

Semi-random links:

Rafi's site:  [http://ofb.net/~rafi/latitude_xt.html](http://ofb.net/~rafi/latitude_xt.html)

Matthew's blog:  [http://www.advogato.org/person/mjg59/diary.html?start=198](http://www.advogato.org/person/mjg59/diary.html?start=198)

messing with hotkeys:  [http://bugzilla.kernel.org/show_bug.cgi?id=11424](http://bugzilla.kernel.org/show_bug.cgi?id=11424)
[http://www.nvnews.net/vbulletin/showthread.php?t=118562](http://www.nvnews.net/vbulletin/showthread.php?t=118562)

Edit:  Radeon seems pretty stable.  I don't think it supports 3-D/Compiz yet.

---

### Post by synace on 2009-07-10
fglrx w/ the rotate compiz/metacity toggle is working well for me (just need the bezel button now! :))


i thought radeon 'could' support compiz.. 

[http://ubuntu-unleashed.com/2008/04/howto-setup-compiz-fusion-with-open-source-ati-radeon-drivers.html](http://ubuntu-unleashed.com/2008/04/howto-setup-compiz-fusion-with-open-source-ati-radeon-drivers.html)

---

### Post by synace on 2009-07-10
lshal has some interesting things in there.. perhaps setting the keyboard to another type (extended of somekind) will allow those 3 side buttons?

as per: [http://www.nvnews.net/vbulletin/showpost.php?p=1764019&postcount=2](http://www.nvnews.net/vbulletin/showpost.php?p=1764019&postcount=2)

no acpi events fired on those buttons. :(

you would think HP would have a linux evangelist supporting this stuff.

---

### Post by Favux on 2009-07-10
Hi synace,

Well dragging a launcher into the top panel and getting it down to a single click isn't too bad.  And it has the advantage of working in portrait.  I have one set up to Tom's wacomrotate.  Then one in my dock to my script and one using the same script to my bezel button "Q" key.  Redundancy.  And I've modified the scripts to kill and restart my cairo-dock because it doesn't resize correctly on reorientation.

I think that's wrong.  They keep promising radeon support for Compiz but I don't think it's happened.  But I could be wrong.

Some people claim going to the evdev keyboard layout gives them access to buttons and keys that were dead.  So who knows.

Edit:  Yeah I've done all that stuff on my two dead keys and swivel hinge.  Only MisteR2 made progress.  But yours aren't the same so it's worth double checking everything.
Edit:  Especially since they sell linux pre-installed.  I've given up trying to understand why the OEM's do what they do.  I suspect all sorts of contracts and NDA's, not just economics.

---

### Post by synace on 2009-07-10
think we can isolate the issue of the stylus killing touchscreen effectiveness? if we do, we could add a simple gesture to run a script that resets the input to the same state as a fresh boot of X? (you would fire this gesture when you're putting the stylus away)

note, on fresh boot. rotation w/ compiz/metacity toggle keeps touchscreen accuracy through rotates.

i suppose the same functionality could be used to disable 'touch' input when 'stylus' is inputting...

i think basically what we have here is 'touch' is working 100%. stylus comes to play & breaks everything. let's play w/ the settings in the stylus inputDevice.

---

### Post by Favux on 2009-07-10
Sounds good, I listed them on the other thread.

---

### Post by synace on 2009-07-10
xinput query-state touch
shows x at 9593 and y at 7191 in bottom most corner.

xinput query-state stylus
i can get to 9562 x 7158

xinput query-state touch
shows: 4411 x 5579

at the same time.. so touch never updated w/ the stylus's position.

when i move the mouse...
xinput query-state stylus
shows: 3600 x 4149
xinput query-state touch
shows: 4411 x 5579

so, touch sits. stylus updates.

trying fresh boot to see if touch updates w/ mouse's position before i use stylus.
nope. touch sits still.

---

### Post by Favux on 2009-07-10
Huh...  So what happens if you change window managers without bothering to rotate?

---

### Post by synace on 2009-07-10
not sure .. same as normal? w/ & w/o compiz it functions the same, it's just that with xrandr & compiz, i just see the desktop after rotation & setting compiz. if i rotate w/ compiz on, it's a mis-aligned not really resized view.

also, my 100% functional touch is a bit of a mystery. it's not working anymore :(

---

### Post by Favux on 2009-07-10
Bummer.

I must have misunderstood you.  I thought you were saying rotating and changing window managers was giving you touch sensitivity back.  So I was wondering did xrandr need to be involved?  Could just changing window managers do it?  Because that would make an easy workaround.

In landscape alternate Compiz to metacity (and back?) and in portrait metacity with xfwm4, which I know works in portrait, (and back?).

---

### Post by darco on 2009-07-10
Can someone help the OP? :lolflag:

darco

---

### Post by synace on 2009-07-10
darco, i told angel to uninstall the new kernel as i instructed in a previous post. also angel should try my xorg.conf file (assuming they've installed the fglrx driver).

---

### Post by darco on 2009-07-10
heh...must have lost that in skimming thru all those posts!

darco

---

### Post by angel120 on 2009-07-12
Unfortunately, I couldn't even boot into my old kernels, so I just took the plunge and formatted the partition.  I spent all day Friday trying the instructions posted in this thread, and no such luck.  Every single time I tried booting into the newly modified kernel, I'd see the same exact thing happen w/ the splash screen.  No idea what's going on..  Makes me feel like I'm not allowed to use my tablet in Ubuntu LOL.

EDIT: Later today, I'm going to try the things that synace posted here.  I actually didn't see them before, and it kinda gives me some hope that I'll have some luck with this..

---

### Post by Favux on 2009-07-12
Hi angel120,

Hopefully synace is around to day and will help you out.

From what he was saying it sounded like it may be an ATI video issue.  Are you able to get to your xorg.conf in the install that is failing and post it?

---

### Post by angel120 on 2009-07-12
Favux,

I completely reformatted the failing install, and am now working with a fresh 9.04 w/ 2.6.28-13-generic kernel.

I followed synace's steps in post #22 as he listed it (installed the headers & image that he linked, in that order), then copied over his exact xorg.conf, and then rebooted.  I see the splash screen, and the progress bar goes all the way through, then the screen turns black and no response from keyboard input.  The only way I was able to shut it down was by holding down the power button.

I just restarted my laptop and am trying the same (patched) kernel again, and the same thing happens.  Restarting again, and trying 2.6.28-11-generic yielded the same results.

I just replaced synace's xorg.conf with my original one (via recovery mode) and booted back into the patched 2.6.28-13-generic, and I'm able to log in.  Touch is recognized, but severely out of calibration.  Same thing applies to my stylus.  What should I try next?

---

### Post by Favux on 2009-07-12
Hi angel120,

Outstanding!  So you've got gui.

Just post or attach your current working xorg.conf.  And in the meantime run Update Manager and see if it wants to do updates.  Obviously don't let it do any that involve the kernel or kernel headers etc.  And if you see one that has something to do with xserver-xorg let me know.

---

### Post by angel120 on 2009-07-12
Favux, here's my (working) xorg.conf..

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

Update Manager wants me to update the kernel headers and image, but nothing about xserver.

Thanks for your help, by the way ):P

---

### Post by Favux on 2009-07-12
Hi angel120,

Not a problem.

First be sure to back up the xorg.conf and be ready to restore it from the command line.  Keep track of them and doing that with each one so you can restore from the last working one.

First let's try the Wacom sections but without "ServerLayout".

---

### Post by angel120 on 2009-07-12
I used your xorg.conf, and the computer booted successfully, but my touch and stylus have not changed behavior.  

Touching the screen doesn't make the cursor move to where my finger is, but if I drag my finger across the screen, the cursor will move in the same direction, but not with it.  

Same thing happens with the stylus.  The stylus doesn't left nor right click, either.

---

### Post by Favux on 2009-07-12
Hi angel120,

I'm doing it in installments so if there's a problem we can localize it.

Now let's try adding an Intrepid style "ServerLayout".  X breakage much more likely this time so back up the test 1 xorg.conf above and be prepared to restore it from the command line.

---

### Post by angel120 on 2009-07-12
Favux, test 2 lead to a black screen after the splash.

---

### Post by Favux on 2009-07-12
Hi angel120,

OK, so we've localized it to "ServerLayout".

We know the wacom lines work for other TX2z's in Jaunty.  But there was a bug in xserver-xorg that seemed to cause X breakage if wacom entries were in "ServerLayout" when Jaunty first came out.  It didn't happen to everyone and I couldn't see a pattern.  I thought they fixed it which is why I wanted to know if Update downloaded a newer xserver-xorg or something similar.

So let's assume it's something to do with the video lines.  So try the test 3 below.

By the way yours is a fresh install, correct?  You didn't upgrade the first time either?

---

### Post by angel120 on 2009-07-12
Hey, Favux..

The third test also yielded the same result.  Didn't boot, so I had to restore my prior xorg.conf (test #1).

To be honest, I don't remember if I updated xserver-xorg, but I know I installed all the updates when I first booted into Ubuntu.

Side note, how do I stop Update Manager from asking me to install linux-headers-2.6.28-13-generic and linux-image-2.6.28-13-generic each time I boot up?

---

### Post by Favux on 2009-07-12
Hi angel120,

OK, so if it's video...  Ayuthia mentioned something about having to reinstall "fglrx" so let's see if that works.  Go to Hardware Drivers and uninstall the ATI proprietary drivers and then reinstall them.  Then retry test 2 and if that doesn't work test 3.

Right now after you use the stylus touch becomes intermittent.  If you swipe two fingers across the screen you can get touch "back".  Everybody's been trying to figure this out.  Ayuthia announced a couple of hours ago he thinks he has.  He applied a fix to one of the patches and now it's working.  If it keeps working he'll update the instructions and kernel deb.s, hopefully tomorrow.  And with luck it will be with the new kernel Update Manager is nagging you with.  So keep an eye out.

---

### Post by angel120 on 2009-07-13
Favux,

I uninstalled fglrx, reinstalled it, rebooted, and retried test 2, which didn't work..  Did the same for test 3, and I had the same result.  

I then uninstalled fglrx, reinstalled it, put in test 2, and then rebooted, and still got the same result.  Did the same for test 3, and again, no dice.

For me, touch is not intermittent.  If I hover with the stylus, move the stylus away, then use my finger, the touch is still registered.  No need for a 2-finger swipe.  Then again, my touch/stylus isn't working properly yet, so that may be why I'm seeing different results in that respect.

To be honest, I'm much more interested in getting the stylus to work 100% so I can finally use my tablet in Linux.  When I had 8.10, I was able to get the touch and stylus to work 100%, but when I tried writing in Xournal, the page would jump around violently, making it impossible to write anything coherent.

---

### Post by Favux on 2009-07-13
Hi angel120,

Sounds like you'll have that in a day or two and Ayuthia is patching on the latest kernel.  Stylus works 100% with current patched kernel.  It's just touch that can be iffy.

So the ATI driver seems to be installing without problems.

Let's see if it wants the Direct Rendering Infrastructure (DRI) line.

---

### Post by synace on 2009-07-13
> **Favux said:**
> Hi angel120,
Sounds like you'll have that in a day or two and Ayuthia is patching on the latest kernel.  Stylus works 100% with current patched kernel.  It's just touch that can be iffy.

Ayuthia is providing an updated patched kernel? 64bit? :)

---

### Post by Favux on 2009-07-13
Hi synace,

That's what it looks like, but he may have found a problem with multitouch (two fingers).  He's going to take that line out.  We'll have to see.

---

### Post by angel120 on 2009-07-13
> **Favux said:**
> Hi angel120,

Sounds like you'll have that in a day or two and Ayuthia is patching on the latest kernel.  Stylus works 100% with current patched kernel.  It's just touch that can be iffy.

So the ATI driver seems to be installing without problems.

Let's see if it wants the Direct Rendering Infrastructure (DRI) line.

Hey, Favux.  First, I'd like to thank you for your patience.  My laptop doesn't seem to want to cooperate with what seemingly works with all the other TX2's lol

Unfortunately, test #4 didn't work, either.  Still the same thing w/ the black screen after the splash.  I didn't try reinstalling fglrx though, maybe I should try that next?

Another issue with my laptop, though not important, is the fact that my microphone doesn't work, but my speakers work fine.  Were you able to get it to work properly?  I remember in the other Touchsmart thread, you had a lot of issues with sound in Intrepid..

---

### Post by Favux on 2009-07-13
Hi angel120,

No, I don't think you need to reinstall ATI proprietary ("fglrx").  I think that is suppose to be a one time thing if the kernel deb causes problems.

Just about out of ideas.  Let's go back to your original video except the two new video lines in "ServerLayout" and comment out "SendCoreEvents".

---

### Post by angel120 on 2009-07-13
Favux, when did you start modifying your xorg.conf files for your install?  Before or after you did the initial update on a fresh install?

By the way, test #5 didn't work, either...  Same result, black screen where the backlight blinks on and off.

---

### Post by Favux on 2009-07-13
Hi angel120,

Alright.  I'm out of ideas.  I suppose you could uninstall the two linuxwacom packages xserver-xorg-input-wacom and wacom-tools, reboot, reinstall them, and reboot.  See if that does anything.

I don't understand why you're having the problem.  I suspect some sort of install glitch.  ATI could be involved.  The other thing is for Jaunty we had to substitute a 0.8.3-x wacom.ko (the usb kernel driver) for the default Jaunty 0.8.2-2 wacom.ko.

Do you have Vista installed?  Have you installed Win7?  I ask because the N-trig firmware is different between the two.  Also have you checked to see if there is a bios update?

I don't have a TX2z, I have a TX2000 with Nvidia.  I leave my xorg.conf in place when I recompile linuxwacom:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by angel120 on 2009-07-13
> **Favux said:**
> Hi angel120,

Alright.  I'm out of ideas.  I suppose you could uninstall the two linuxwacom packages xserver-xorg-input-wacom and wacom-tools, reboot, reinstall them, and reboot.  See if that does anything.

I don't understand why you're having the problem.  I suspect some sort of install glitch.  ATI could be involved.  The other thing is for Jaunty we had to substitute a 0.8.3-x wacom.ko (the usb kernel driver) for the default Jaunty 0.8.2-2 wacom.ko.

Do you have Vista installed?  Have you installed Win7?  I ask because the N-trig firmware is different between the two.  Also have you checked to see if there is a bios update?

I don't have a TX2z, I have a TX2000 with Nvidia.  I leave my xorg.conf in place when I recompile linuxwacom:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

I'm in class right now so I'll have to get back to you about the other questions.

I am dual-booting between Ubuntu 9.04 and Windows 7 RC.  I used to have Ubuntu installed via Wubi, but now I put Ubuntu in a 50GB partition.

---

### Post by Favux on 2009-07-13
Hi angel120,

OK, that may be the problem.  The new Win7 N-trig firmware.

Let's see if the by-path is different:
```
lsinput |& grep -iB2 1b96
```
and/or
```
ls -l /dev/input/by-path
```

Edit:  Another thought belatedly occurs.  As Ayuthia said to, you did remove the N-trig section from the 10-wacom.fdi, correct?

---

### Post by angel120 on 2009-07-13
Favux,

I'll check those 2 commands as well when I get home.

I tried commenting out the N-Trig section from the .fdi, but I wasn't sure if I had to comment out the whole N-Trig section, or just the line that says "Stylus" from within the N-Trig section.  To me, that area in the tutorial was a little ambiguous..

I originally tried commenting out the entire N-Trig section before starting this thread, as well as only commenting out the stylus line from within.  Both yielded the same result.

---

### Post by Favux on 2009-07-13
I'd make a backup of the 10-wacom.fdi and then either remove the N-trig section or the whole .fdi.  What we don't want is the n-trig match lines starting to configure anything.

---

### Post by angel120 on 2009-07-13
Oh ok, so just to make sure I got it right, either comment out the N-Trig section, or comment out all lines within the .fdi?

How does the .fdi file work?  Does it configure other things based on what's listed within the .fdi?  So, if I comment out the entire .fdi, it'll essentially rewrite itself?

---

### Post by Favux on 2009-07-13
It'll only configure things in lshal (your hardware) that match it's match lines.  The N-trig subsection looks like:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
```

---

### Post by angel120 on 2009-07-13
Favux, here's my output for the 2 commands you told me to try:

```
angel@angel-ubuntu-HP:~$ lsinput |& grep -iB2 1b96
bash: syntax error near unexpected token `&'
angel@angel-ubuntu-HP:~$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root 9 2009-07-13 21:34 pci-0000:00:14.5-usb-0:2:1.1-event-mouse -> ../event7
lrwxrwxrwx 1 root root 9 2009-07-13 21:34 pci-0000:00:14.5-usb-0:2:1.1-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2009-07-13 17:34 platform-i8042-serio-0-event-kbd -> ../event5
lrwxrwxrwx 1 root root 9 2009-07-13 21:34 platform-i8042-serio-1-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2009-07-13 21:34 platform-i8042-serio-1-mouse -> ../mouse2

```

I changed my 10-wacom.fdi (took out the entire N-Trig section) before doing those 2 commands, and now I'm going to restart using Test #3.  Wish me luck!

EDIT: Taking out the entire N-Trig section in the fdi and using xorg test #3 did not work.  Yielded the same exact result as before.  So I only restored xorg.conf and rebooted while still using the same fdi, and I was able to boot successfully.  Finger and stylus input still respond the same way as before, however.

---

### Post by Favux on 2009-07-13
Hi angel120,

Luck!

And I think you may have to change the by-path's in stylus and touch from:
```
Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
```
to
```
Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-mouse"
```
We probably want to see what this looks like:
```
dmesg | grep [Ww]acom
```

Edit:  I don't know what you mean:
> restored xorg.conf and rebooted while still using the same fdi, and I was able to boot successfully. Finger and stylus input still respond the same way as before

---

### Post by angel120 on 2009-07-13
Yay! That gives me hope! So uh... where do I edit those lines? I'm sorry, I'm just very new to linux in general..

The command you told me to try doesn't do anything..  Is it because I'm using my modified .fdi?
```

angel@angel-ubuntu-HP:~$ dmesg | grep [Ww]acom
angel@angel-ubuntu-HP:~$ dmesg | grep wacom
angel@angel-ubuntu-HP:~$ dmesg | grep Wacom
angel@angel-ubuntu-HP:~$ 

```

---

### Post by Favux on 2009-07-13
Hi angel120,

Sorry, I meant the two Wacom sections stylus and touch in xorg.conf.
```
gksudo gedit /etc/X11/xorg.conf
```

The dmesg being blank means the wacom.ko isn't getting anything, which I figured since we don't have xorg.conf working yet.

I feel compelled to mention if you are willing to give up on touch for now and go with just the stylus and the stylus button we should be able to get you set up that way.

---

### Post by angel120 on 2009-07-13
Thanks, Favux!

I just edited those 2 lines in my working xorg.conf and am rebooting right now.  Let's see what happens..

I honestly don't care so much about touch at the moment (multi-touch is a different story..), but if I can just have my stylus working 100% like it does in Windows 7, then I'll be extremely happy!

So my laptop just came back on, and I was able to boot to my desktop.  As for touch and stylus, both of them work in the exact same manner.  However, I'm gonna go back and edit all 5 xorg's that you send me, and try each one of them.  Hopefully it'll get us somewhere!

EDIT: Here are the results of my tests:
xorg test #1 - booted fine, touch and stylus remain the same

xorg test #2 - booted fine, touch and stylus WORK!!!
        Xournal - Pressure sensitivity works, and the page doesn't jump around when I put my palm on the screen.

xorg test #3 - booted fine, touch and stylus work, but feels a little difficult at times (my pen may or may not be damaged)

xorg test #4 - booted fine, touch and stylus work in the same way.

xorg test #5 - booted fine, touch and stylus work in the same way.
Note: My 10-wacom.fdi still has the entire N-Trig section removed, and the xorg.conf's by-path has been edited.

---

### Post by Favux on 2009-07-13
Hi angel120,

Wow!  It works!  It was the by-path all along!?  Test 2 is basically your original booting xorg.conf with the wacom/n-trig stuff added plus "ServerLayout".

Edit:  Test 3 swapped Ayuthia's single line "ServerLayout" entry for the two "video lines" in the test 2 "ServerLayout".

Edit:  Totally cool.  Thanks for doing that.  I'd go with the test 2 version unless you have a reason for another one.

---

### Post by angel120 on 2009-07-13
Bumping so people can check out post #78.

I want to thank you, Favux, for all your help these past few days.  I'm so glad to finally be able to get my stylus and touch working, and I wouldn't have been able to do it without your help!

Just to recap, here's what fixed the situation:
[list]
[*]Remove the entire N-Trig section in 10-wacom.fdi
[*]Change xorg.conf to test #2, 3, 4, or 5
[*]Change the by-path in the touch & stylus sections within xorg.conf
[/list]

One more thing, is there a way to disable touch? I'm thinking of putting a launcher in the panel, so when I'm writing my notes in class, I can just click on the launcher to disable touch, and freely write my notes without any nuisance.  Of course, if there's no way, then I'd gladly disable touch altogether until a solution is found..  By the way, how would I disable touch altogether? Simply comment out the "touch" sections within xorg.conf?

---

### Post by Favux on 2009-07-13
Hi angel120,

You're welcome.  Like I said I'd use test 2, which is basically your original xorg.conf unless you have a reason/want a different one.  I'm not confident test 5 with "SendCoreEvents" commented out will be stable.

And remember we had to change the by-path because you had the Win7 firmware, not the Vista firmware.

I'm not sure you can turn touch off with your set up.  You should be able to with:
```
xsetwacom set touch touch off
```
And then to turn it back on the same but off to on.  But I think some other folks with n-trig and Ayuthia's patched kernel said it wasn't working for them.  But worth trying.

Again not sure you can disable touch altogether with n-trig.  But first I would try to comment out (#) the touch entry in "ServerLayout".  If that doesn't work I'd keep it commented out and then move onto the touch section.  If you try to comment out the touch section you'll knock out the tablet coordinates.  So you would have to try moving them to the stylus section.

---

### Post by angel120 on 2009-07-14
Favux, thanks!

I tried that command, but unfortunately, 'xsetwacom' is not installed.

The next post I put on here will be a "how to" for this entire ordeal, just in case I have to reformat my laptop before 9.10 comes out and/or if someone else is having difficulty with their own TX2.

Again, Favux, thanks a million!

---

### Post by Favux on 2009-07-14
Hi angel120,

Check Synaptic Package Manager.  We know the 0.8.2-2 linuxwacom driver package xserver-xorg-input-wacom is installed.  Make sure wacom-tools is also installed.

---

### Post by angel120 on 2009-07-14
This is a quick summary of the entire process mentioned in this thread.  This is for reference for either myself, or anyone else with an HP TouchSmart TX2 that is having trouble getting their touch input or stylus to work properly.

First off, my specifications:
[list]
[*]HP TouchSmart TX2z 1025, purchased Feb 2009
[*]AMD Turion X2 @ 2.1GHz, 4GB RAM, 320GB hard drive, webcam, fingerprint scanner
[*]Dual booting between Ubuntu 9.04 64bit with (patched) 2.6.28-13-generic & Windows 7 64bit Release Client (installed May 2009)
[/list]

Steps:
[list]
[*]Get everything else working via [http://ubuntuforums.org/showpost.php?p=6953032&postcount=72](http://ubuntuforums.org/showpost.php?p=6953032&postcount=72) (ignore steps 4, 8, 9, 10, 11, 14)
[*]Download Ayuthia's patched kernel to ~/Desktop
Image: [http://linuxfans.betaserver.org/packages/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb](http://linuxfans.betaserver.org/packages/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb) 
Headers: [http://linuxfans.betaserver.org/packages/linux-headers-2.6.28-13-generic_2.6.28-13.44_amd64.deb](http://linuxfans.betaserver.org/packages/linux-headers-2.6.28-13-generic_2.6.28-13.44_amd64.deb)
[*]Download my 10-wacom.fdi & xorg.conf (see attached) to ~/Desktop
[*]Take out .txt from both aforementioned files (rename them)
[*]Run the following 3 commands:
```

sudo dpkg -i ~/Desktop/linux-headers-2.6.28-13-generic_2.6.28-13.44_amd64.deb && sudo dpkg -i ~/Desktop/linux-image-2.6.28-13-generic_2.6.28-13.44_amd64.deb
sudo rm /etc/X11/xorg.conf && sudo cp ~/Desktop/xorg.conf /etc/X11/
sudo rm /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi && sudo cp ~/Desktop/10-wacom.fdi /usr/share/hal/fdi/policy/20thirdparty

```
[*]Reboot and test
[/list]

PS - If there's anything I missed or any mistakes I made, please don't hesitate to let me know!

Special thanks to Favux for helping me out!

---

### Post by Favux on 2009-07-14
Hi angel120,

I guess the plan is to integrate MPX and some other multitouch stuff into the next few releases of Xserver.  So I don't know for sure what will be ready for Kharmic (9.10).  It may be an "experimental" option.  But Kharmic will have 2.6.31 which already had pretty good N-trig support.  And if Rafi, Ayuthia, and the others track down the last niggling issue it may even rock.

Let's see if we can turn touch off.  Attached is the simplest way in the xorg.conf I can think of.

---

### Post by synace on 2009-07-15
you'll see that your test #2 is the same as the one I ended up posting (though, i'm still using /dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse.. probably different firmware version?).

i looked though your changes vs mine, and the only difference i could determine was the commenting out of ntrig in the fdi file. i applied that change,

now my touch works 100% perfect. 

when i bring the stlyus in range, it takes over (still doesn't get rid touch though/aka no palm recognition... still can't use xournal). but then touch goes back to the way it used to be (kinda crappy). i can get it to go back to awesome by dragging 2 fingers across the screen about 2 inches apart.

disabling/re-enabling it works for me:
```

xsetwacom set touch touch off

```
```

xsetwacom set touch touch on

```

any chance we can further patch the ntrig stylus driver to trigger these when the stylus is in range?

i have a feeling that the 'kinda crappy' response of touch is actually the functionality of palm recognition. the problem is that ANY drag during this state is registered. so, it's not a very effective touch disable while the stylus is in play.

---

### Post by synace on 2009-07-15
for now i've added icons to my panel to fire the tablet rotation and the touch on/off

the rotate is in one of my previous posts...

the touch toggle:

```

#!/bin/bash
STATUS=`xsetwacom get touch touch`
if [ "$STATUS" == "0" ]
  then
    echo "Touch was OFF, enabling."
    xsetwacom set touch touch on
else
    echo "Touch was ON, disabling."
    xsetwacom set touch touch off
fi

```

any1 know how to get this conditional working for /bin/sh? i have it for bash here

---

### Post by synace on 2009-07-15
i notice now my calibration is off in tablet/inverted tablet (portrait/reverse portrait) positions.

landscape (normal) and inverted landscape (180degrees?) are both fine.

also, right click (xournal eraser) doesn't work when your palm is resting on the surface.

cellwriter works well!

issues with the touch not being 100% responsive, i find that a 'pinch' seems to correct the touch better than 2 fingers dragging across the screen. place forefinger & middle finger as far apart as you can and then pinch them together. touch works immediately after this.

---

### Post by svelter on 2009-07-15
Hi, all.  I apologize if this post is slightly off topic. Going way back to the very first post of this thread, I am getting the same screen (funky neon green ubuntu logo with frozen status bar below) when I boot up.  This just happened this evening for the very first time.

I know recently this thread has been about touch screens, but I don't have one of those.  I have a regular old laptop.  HP Pavilion dv4000 series.  Intel Pentium M at 2.13 GHz; ATI mobility radeon graphics.  

I had been running ubuntu 8.10 for a while.  I didn't upgrade at first when 9.04 became available, but yesterday I thought I would bite the bullet and upgrade.  I did so and everything was running just fine last night.  Today when I tried to boot up, I got the neon green funk.  

I'm a relative noob when it comes to linux, but i'm doing my best to keep up.  I've read through a few threads, but have gotten nothing to work.  Here's what I've tried so far:


[LIST]
[*]pressing esc to enter GRUB menu, I have tried all the options listed (kernel 2.6.28-13-generic; same kernel in recovery mode; kernel 2.6.27-14-generic; same kernel in recovery mode)
[*]running dpkg, i get a long list of errors (failed to fetch various items from various URLs; some index files failed to download; you way want to run apt-get update to corect these problems).  it tells me it will upgrade wine and wine-gecko.  I agree, and it fails to fetch the items
[*]have chosen items to update grub bootloader and xfix to auto repair graphic problems
[*]dropped to root and ran apt-get update.  fails to retrieve all items and tells me to run apt-get update to correct the problems.
[*]entered the following at root:
sudo dpkg-reconfigure xserver-xorg
[LIST]
[*]went through all steps to no avail
[/LIST]
[*]downloaded the .iso and burned to CD.  through boot menu, booted from hard drive with various options selected (acpi=off; noapic; nolapic).  none worked.
[/LIST]
I get no sound or visual (other than the neon green), so I don't think it's strictly a graphics issue.  I can boot from CD as a liveCD, but would really like to fix my installation without reformatting, if possible.  

I haven't read in depth through all the posts, as it seems like the last several pages were specific to resolving touch screen functionality.  But please correct me if i'm wrong.

I'd really appreciate any help anyone can offer.  Thanks so much in advance.

---

### Post by Favux on 2009-07-15
Try
```
#!/bin/sh

if [ `xsetwacom get touch Touch` -gt 0 ]
then
	xsetwacom set touch Touch 0
else
	xsetwacom set touch Touch 1
fi
```

---

### Post by synace on 2009-07-15
> **Favux said:**
> Try
```
#!/bin/sh

if [ `xsetwacom get touch Touch` -gt 0 ]
then
	xsetwacom set touch Touch 0
else
	xsetwacom set touch Touch 1
fi
```

works! the bash one works for me as well ;)

i've added a rotate button, a touch toggle and a gps toggle (hotplug for the gps isn't exactly functional).

---

### Post by svelter on 2009-07-15
**EDIT: just realized that post may not have been for me... **

Thanks, Favux.  I did try that, but got the following message:
[INDENT]The program 'xsetwacom' is currently not installed.  You can install it by typing:
apt-get install wacom-tools
bash: xsetwacom: command not found

[/INDENT]I did type in the suggested command.  it tells me it will install 5 new packages.  I agree.  A series of errors ensues (such as "Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main tc18.4 8.4.19-2 could not resolve us.archive.ubuntu.com).  It suggested I try the same command with --fix-missing.  I did this, but it also didn't work.

Am I doing something wrong to cause these repeated errors?

---

### Post by synace on 2009-07-15
> **svelter said:**
> **EDIT: just realized that post may not have been for me... **

Thanks, Favux.  I did try that, but got the following message:
[INDENT]The program 'xsetwacom' is currently not installed.  You can install it by typing:
apt-get install wacom-tools
bash: xsetwacom: command not found

[/INDENT]I did type in the suggested command.  it tells me it will install 5 new packages.  I agree.  A series of errors ensues (such as "Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main tc18.4 8.4.19-2 could not resolve us.archive.ubuntu.com).  It suggested I try the same command with --fix-missing.  I did this, but it also didn't work.

Am I doing something wrong to cause these repeated errors?

that was actually regarding my post about the tablet PC stuff, disregard.

your issue is probably related to video configuration. boot to a 'recovery' console as root, and edit your /etc/X11/xorg.conf file. switch to the 'vesa' driver if possible.

```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backuptest
cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
exit

```

then continue with normal boot.

---

### Post by svelter on 2009-07-15
Hi, Synace.  Thanks so much.  I'm not sure if I'm missing a step somewhere, but when I type in what you have above (cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backuptest), I get the following response:

cp: cannot stat `etc/X11/xorg.conf': No such file or directory

any idea why I might get that response?

---

### Post by synace on 2009-07-15
> **svelter said:**
> Hi, Synace.  Thanks so much.  I'm not sure if I'm missing a step somewhere, but when I type in what you have above (cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backuptest), I get the following response:

cp: cannot stat `etc/X11/xorg.conf': No such file or directory

any idea why I might get that response?

this is being done in the recovery console as root? did you forget the leading "/" ?

p.s. i typed this using the touch input through the keys feature of cellwriter!

---

### Post by svelter on 2009-07-15
> **synace said:**
> this is being done in the recovery console as root?

p.s. i typed this using the touch input through the keys feature of cellwriter!

it is.  and just to make sure, i logged in and tried it that way as well.  

actually, i just rebooted and tried again, and this time i didn't get any errors.  I tried to boot normally, but am still getting the neon green logo issue.

curses...

---

### Post by Favux on 2009-07-15
Hi svelter,

Sorry about the mix up.  Are you sure you have ATI mobility radeon graphics and not Intel 915GM?  I've seen some DV4000's with the Intel.  And Intel has some problems with Jaunty.  Or if there was an option for an add-on ATI card have you checked the bios that you've disabled the motherboard video (intel) and enabled the ATI card?

Either way if you know the exact name for the graphic card we could google it and see if there are known install problems.  Someone may have posted a work around.  I agree with synace that it's probably a graphics problem.

---

### Post by svelter on 2009-07-15
Hi, Favux.  No worries - my eagerness got the better of me.  :)

Unfortunately, my BIOS doesn't have any information on which graphics card is active.  You're probably right - it's probably reading the integrated intel card and not the ATI.

I was taking a look at an intel thread ([this one]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=edit+xorg.conf")), but can't make it through step one for some reason.  Perhaps I'll take up the issue there, since this appears to be unrelated to this thread now.  That, or I may see if I can salvage my files somehow and just go back down to the 8.10 release.  We'll see how ambitious I feel over the next couple of days...

Thank you both for all of your help!  I really appreciate it.

---

### Post by angel120 on 2009-07-15
Favux,

YOU ARE MY HERO!!!  I FINALLY have my laptop working just the way I wanted it to!  Thank you SO much for all your help!

I used your 6th xorg.conf, and now touch is entirely disabled and only the stylus works.  Writing in Xournal is perfect, I dont have to worry about accidentally hitting any of the buttons or menus (I'm a lefty), and no more lines bouncing all over the place.

I simply cannot thank you enough for all your help, Favux!  I can only hope someday I'll be as linux-savvy as you are.

Now for a side-note.  This doesn't quite have to do with the current topic, albeit it is Video-driver related..
I'm a computer science major, and I'm taking an OpenGL class (programming in C++).  I have the GLUT libraries and whatnot installed, and I'm using the Code::Blocks IDE.  Whenever I try to run my OpenGL programs in my current setup, the programs compile fine but the program itself is in an "invisible" window.  When my OpenGL program opens, I can see a quick (1 second or less) flash of the correct output, but then it becomes invisible.  If I move my mouse to where the tilebar is, I'm able to move the window and resize it, and it again flashes for 1 quick second, but then disappears.

My desktop had the same problem (has an ATi Radeon HD2600XT by HiS), which was fixed by going to ATi's website and downloading their Linux drivers.  After updating the driver, I'm able to see the window open up, but it remains blank until I resize the window.  After resizing the window, the image suddenly appears.  However, when I maximize the window, GNOME seems to crash (able to move the mouse but nothing responds to any input).

My laptop has an ATi HD3200 graphics card.. Would updating my graphics drivers cause our whole fix to go out the window?  I think when I made my original post in this thread, I was using the graphics drivers from ATi's website...

Also another side note, but entirely different topic, I am still having trouble setting up my microphone..  On skype, no one can hear me!  But I think that should be set aside in a different thread...

Again, Favux, thank you SO much for all your help :)

---

### Post by Favux on 2009-07-15
Hi angel120,

Great!  You are welcome.  It's an illusion, I just know a little Wacom and xorg.conf stuff.  If you're a Comp. Sci. major in a few weeks you'll know more, if they give you the time.  ;)

I don't know much about ATI or OpenGL for that matter.  I know ATI drivers can be problematic.  Maybe it needs a little configuring.  You could look at:
```
glxinfo | grep render
```
and of course
```
glxinfo
```
and see if that gives you any clues.

I don't think changing the driver should affect anything we've done.  But just in general it's a good idea to be careful with updating ATI.  Here's some links:

The Unofficial ATI linux driver wiki's Jaunty page:  [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Ubuntu's "unofficial" Jaunty driver update page (because they know there's been some driver problems in Jaunty):  [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

I don't remember seeing anything about the TX2z's microphone, I'll try to keep an eye out.

---

### Post by angel120 on 2009-07-15
Favux, here's my output:

```

angel@angel-ubuntu-HP:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: ATI Radeon HD 3200 Graphics 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_copy_depth_to_color, 

```

```

angel@angel-ubuntu-HP:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_import_context, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_allocate_memory, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_import_context, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_swap_control, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics 
OpenGL version string: 2.1.8575
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_AMD_performance_monitor, GL_ARB_color_buffer_float, 
    GL_ARB_depth_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_draw_instanced, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_instanced_arrays, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_buffer_object, GL_ARB_texture_compression, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_transpose_matrix, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_buffer, GL_EXT_copy_texture, 
    GL_EXT_draw_buffers2, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_integer, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_texture_swizzle, 
    GL_EXT_transform_feedback, GL_EXT_vertex_array, GL_KTX_buffer_region, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_copy_depth_to_color, 
    GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_WIN_swap_hint, 
    WGL_EXT_swap_control

65 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x43 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x9d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  4 1 Ncon

71 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x43  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x58  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x59  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x5b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x60  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x61  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x62  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x63  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x64  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x65  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x66  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6c  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x6d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x6e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x9d  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  4 1 Ncon
0x9d  0 tc  0 128  0    y  . 32 32 32 32  0 24  0  0  0  0  0  0 0 Ncon
0x9d  0 tc  0 128  0    .  . 32 32 32 32  0 24  0  0  0  0  0  0 0 Ncon
0x9d  0 tc  0 64  0    y  . 16 16 16 16  0 24  0  0  0  0  0  0 0 None
0x9d  0 tc  0 64  0    .  . 16 16 16 16  0 24  0  0  0  0  0  0 0 None
0x9d  0 tc  0 32  0    y  . 11 11 10  0  0 24  0  0  0  0  0  0 0 None
0x9d  0 tc  0 32  0    .  . 11 11 10  0  0 24  0  0  0  0  0  0 0 None

```

I will add more to this reply when I get on campus.  (sorry, in a bit of a rush!)

---

### Post by synace on 2009-07-15
try nopat on your kernel boot line

---

### Post by Favux on 2009-07-16
Hi everyone,

Ayuthia posted the new 2.6.28-13.45 kernels deb.s on post #186 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=19](http://ubuntuforums.org/showthread.php?t=1038898&page=19)  So touch should be more responsive and you have the latest kernel.

---

### Post by deadspider187 on 2009-07-23
I followed Angel120's summary of steps and am still having issues with stylus and touch.  It seems the cursor is moving faster then my stylus or finger.  I also tried the newer 2.6.28-13.45 with no luck.  Setting the mode to relative or absolute doesn't seem to change this, or, is this not what I need?

---

### Post by erik.kugel on 2009-07-23
Hi Guys, not sure if this helps but I thought FGLRX is not working with newer than 2.6.26 kernels, and with my ATI 3200 I had to use radeon or radeonhd driver. Could that be why the upgrade of the kernel broke fglrx?

---

### Post by deadspider187 on 2009-07-24
Well, I basically reverted all the steps I tried earlier just to get the stylus working again (which was working with a default 9.04 install), but it still is having the issue of using my touchscreen as a trackpad.  There must be some leftover residue from those patched kernel packages.  Any ideas?

Since this was the only thing holding me back from a 9.10 A3 install, I guess I'll be upgrading.  I tried A2 before, and the touchscreen doesn't work with 2.6.31, not even the stylus.  

I have the tx2-1025dx.

---

### Post by Favux on 2009-07-24
Hi deadspider187,

Two things come to mind.  Did you comment out the n-trig section of the 10-wacom.fdi?  And do you have the Win7 firmware like angel120?  Or the Vista firmware?

I'd use the latest kernel deb.s by Ayuthia.

---

### Post by deadspider187 on 2009-07-24
> **Favux said:**
> Hi deadspider187,

Two things come to mind.  Did you comment out the n-trig section of the 10-wacom.fdi?  And do you have the Win7 firmware like angel120?  Or the Vista firmware?

I'd use the latest kernel deb.s by Ayuthia.

Hi Favux,

I used the .fdi from angel120's link.  Should n-trig be commented or not?  I've tried it both ways.  I have an n-trig device, so I would think it should be uncommented.  

I have the Vista firmware.  Do I need the Windows 7 firmware for these steps to work?  I don't currently have a partition to put windows on...

---

### Post by Favux on 2009-07-24
Hi deadspider187,

Since you are using the xorg.conf and 3 others (including Ayuthia) report the .fdi interfers I'd comment it out.

No you don't need the Win7 firmware, but the by-path is different.  See near the bottom where the xorg.conf's are attached here:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

---

### Post by deadspider187 on 2009-07-24
> **Favux said:**
> Hi deadspider187,

Since you are using the xorg.conf and 3 others (including Ayuthia) report the .fdi interfers I'd comment it out.

No you don't need the Win7 firmware, but the by-path is different.  See near the bottom where the xorg.conf's are attached here:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

That did the trick!  I'm now on 9.10 with stylus and touch working.

my xorg.conf
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# Setup for HP TX2z.  Switch comments if you have the Dell Latitude XT.

Section "InputDevice"
	Identifier	"stylus"
	Driver		"evdev"
#   The by-path below is for the HP TX2z
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT
#	Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option		"USB"		"on"
	Option		"Type"		"stylus"
	Option		"Button3"	"3"	# make stylus button R mouse click
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"evdev"
#   The by-path below is for the HP TX2z
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
#   The by-path below is for the Dell Latitude XT
#	Option "Device" "/dev/input/by-path/pci-0000:00:13.1-usb-0:2:1.0-event-mouse"
	Option		"USB"		"on"
	Option		"Type"		"touch"
	Option		"Touch"		"on"
	Option		"TopX"		"0"
	Option		"TopY"		"0"
	Option		"BottomX"	"9600"
	Option		"BottomY"	"7200"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"X.org Configured"	# New for Jaunty?  For TX2z not XT?
#	Identifier	"Default Layout"	# Not needed in Jaunty?  For XT not TX2z?
#	Screen		"Default Screen"	# Not needed in Jaunty?  For XT not TX2z?
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection

#   Developed with Ayuthia (using Rafi Rubin's Wacom sections as a starting point).
#   Dell XT "UseFBDev" line default in video Section per Nimless.
```


The trick with 2.6.31 was to use the evdev driver.  Also, I don't know if this helped or not, but I installed xserver-xorg-input-evtouch.

I do have a problem though, the stylus registers being clicked just by being in range of the touchscreen, even if it isn't actually touching the screen, making it kind of unusable.  Any suggestions?

---

### Post by Favux on 2009-07-24
Hi deadspider187,

Sounds like a proximity or threshold problem.  Evtouch may allow adjustment of those but I don't know what the syntax would be.  Try "man evtouch" or see if there's a readme.

Basically I think the problem is you are not using the linuxwacom drivers for Kharmic.  Rafi recommends applying his n-trig.patch to linuxwacom when using kernels 2.6.29 and up.  I think Kharmic has 0.8.3-2, correct.  So see post #155 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=16](http://ubuntuforums.org/showthread.php?t=1038898&page=16)

---

### Post by deadspider187 on 2009-07-26
There doesn't appear to be any settings like that for evdev, and evtouch doesn't seem to have any documentation, and I couldn't find anything online for it.  

What would the configuration be for evdev if I had a mouse that had the left-mouse button held down?  Is there a workaround for that?  That might work for this.

From what I read on x.org's mailing list (the URL escapes me), evdev will be the future xorg driver for hid_ntrig.  So I think getting this to work with evdev will be useful for everyone when Karmic comes in.

---

### Post by Favux on 2009-07-26
Hi deadspider187,

Sorry, I don't know the answer to that.  It's disappointing that there is no documentation for evtouch.  What I can do is point you to the LWP's HOWTO so you can at least see how it works with linuxwacom:  [http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main)  See Sections 5.1 and 9.

It would be great if you could cite a link for plans to make evdev (evtouch?) the future n-trig driver.  I think Ayuthia and Rafi and others are thinking they may have to fork LWP.

Edit:  Here's a couple evtouch links, the first has some installation info.

[http://www.conan.de/touchscreen/evtouch.html#config%22](http://www.conan.de/touchscreen/evtouch.html#config%22)

[https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/317127)

---

