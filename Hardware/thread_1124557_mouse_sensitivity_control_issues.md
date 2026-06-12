---
title: "mouse sensitivity control issues"
date: 2009-04-13
forum: Hardware
---

### Post by spaceBARbarian on 2009-04-13
I am using ubuntu 9.04 fully updated, previously used 8.10. The machine is a DELL Inspiron 9300 laptop.

With both of these releases I have never been able to control the sensitivity of any USB mouse. My main mouse is a Razer Diamondback, a USB optical mouse.  The mouse is detected fine and the left, right and scroll buttons work flawlessly. However, the sensitivity is insanely high, even if I decrease the acceleration and sensitivity settings in System > Preferences > Mouse.
The sensitivity slider has no effect at all, decreasing the acceleration makes the mouse slightly slower, but not nearly enough.

Also the mouse is detected with 32 buttons instead of the 7 it actually has ( according to "xinput list")

I have also tried variants of the "xset m" command (like "xset m 0 0") but found even with the lowest settings the sensitivity is really high making the mouse really irritating to use, especially for image editing.

I know a lot of other people have pointed out that the gnome mouse properties has no effect, but most of them are able to fix their issues using xset, but for me it is not lowering the sensitivity enough

My touchpad on the other hand runs fine, accurate and proper sensitivity.

Is there anything else I can do to make the mouse less sensitive?

---

### Post by spaceBARbarian on 2009-04-13
okay so i read about .fdi files and i am trying to mess around with sensitivity and resolution settings though these.  I have tried the following two setups: 
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
    <match key="info.product" contains="Razer Diamondback Optical Mouse">
      <merge key="input.x11_driver" type="string">evdev</merge>
      <merge key="input.x11_options.Sensitivity" type="int">1</merge>
      <merge key="input.x11_options.Resolution" type="int">800</merge>
    </match>
 </device>
</deviceinfo>
```
The above has no effect on sensitivity, but the new settings do show in the "lshal" output.

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
    <match key="info.product" contains="Razer Diamondback Optical Mouse">
      <merge key="input.x11_driver" type="string">mouse</merge>
      <merge key="input.x11_options.Sensitivity" type="int">1</merge>
      <merge key="input.x11_options.Resolution" type="int">800</merge>
    </match>
 </device>
</deviceinfo>
```
I tried this after reading a forum post about .fdi files (changed x11_driver to "mouse"), it freezes my pointer until i unplug the mouse, how fun :)

Any idea how I should set up this .fdi file ?

---

### Post by spaceBARbarian on 2009-04-16
Can someone please help me out with this, i've tried these steps with two difference mice, but I cant seem to get the speed of the mouse any lower, its really frustrating.

---

### Post by jmtdstoc on 2009-04-18
I have the same problem. Mouse sensitivity is WAY TOO high on 9.04.
Until 8.10 I could use my mouse just fine if I reduced to the minimum the "Acceleration" and "Sensitivity" sliders.
On 9.04 the "Sensitivity" slider does not work and I get a mouse that's too fast to be usable.

I have a Genius XSCROLL 800dpi USB mouse. If I plug in a Microsoft Wheel mouse it works fine. So, i'm wondering if this just happens whith mouses above 400dpi!!!

Kubuntu 9.04 RC and Fedora 11 Beta also have the mouse TOO FAST, so this must be an issue with the new version of X (1.6.0).

---

### Post by GackY2K on 2009-04-20
Same problem here...I've tried a few mice, but after upgrading to 9.04 my mouse, even set on the slowest speed, is well to fast and extremely hard to use.

Please someone help us!

---

### Post by MeanEYE on 2009-04-23
In the 8.10 xset m 1/3 1 worked fine. Now even this doesnt work for me... tho my mouse works just a slightly faster than I am used to... still it's irritating that I can not change mouse speed :/

---

### Post by Fnyar on 2009-04-27
I was having the same problem under 9.04 except my mouse speed was too SLOW. Then, I noticed that it looks like the slider for sensitivity is inverted. This is probably a bug in gnome-control-center.

$ dpkg -S /usr/bin/gnome-mouse-properties
gnome-control-center: /usr/bin/gnome-mouse-properties

---

### Post by nilezon on 2009-05-03
I'm having a Razer Copperhead, set to 2000 DPI and 1000mhz report rate.
It's almost unusable because of the high mouse speed.

---

### Post by levimendes on 2009-05-15
Razer DeathAdder here. Both acceleration and sensitivity are set to slow and low, still too fast...

---

### Post by babuz' on 2009-05-18
Put into your /etc/X11/xorg.conf in the InputDevice section for mouse:

Option      "ConstantDeceleration" "3"

for more info see here
[http://bbs.archlinux.org/viewtopic.php?id=69851](http://bbs.archlinux.org/viewtopic.php?id=69851)
and here
[http://www.x.org/wiki/Development/Documentation/PointerAcceleration#head-863ae9c52fe3658e800daa0e93d3e434190b732d](http://www.x.org/wiki/Development/Documentation/PointerAcceleration#head-863ae9c52fe3658e800daa0e93d3e434190b732d)

cheers

---

### Post by jmtdstoc on 2009-05-18
My xorg.conf does not have an InputDevice section.
What should I do now?

---

### Post by babuz' on 2009-05-20
If you don't have the InputDevice section, you need to create it:

[FONT="Courier New"]Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        [...]
        Option      "ConstantDeceleration" "2"
EndSection[/FONT]

Cheers

---

### Post by Ubunthree on 2009-05-21
This is the only real issue that I've run into with this release so far, but it will prevent me from using Jaunty, if I can't fix it. At the slowest speed that I am able to get, the cursor crosses the entire 1152x864 screen with about a 1/2" movement of the mouse. It works for clicking on things, though not comfortably, but is useless for image editing or any kind of precision work.

None of the xorg.conf modifications that I've found anywhere are working for me. I've tried various combinations of Sensitivity and ConstantDeceleration and AdaptiveDeceleration options, but the mouse will not slow down no matter what I do. And it looks like xset can't use fractions for the acceleration any more, since even something as drastic as [COLOR="DarkRed"]xset m 1/50 1[/COLOR] has no effect.

---

### Post by jmtdstoc on 2009-05-21
babuz' has given us the solution for this problem!!!

The use of the "xorg.conf" is a dead end... it doesn't work... but the second weblink he has given us WORKS!!!

So, in order to use your mouse with acceptable speeds in Ubuntu 9.04 (or Fedora 11) just create a file by this command:
[B]
$sudo gedit /etc/hal/fdi/policy/10-x11-input.fdi[/B]

and inside that file paste the following code:

[B]<match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_options.AdaptiveDeceleration" type="string">7</merge>
</match>[/B]

Note that the number "7" is what works for me.
If you want a faster mouse use "3", for example.
If you want an even slower mouse use "10", for example.

---

### Post by spacemonster on 2009-05-21
> **jmtdstoc said:**
> babuz' has given us the solution for this problem!!!

The use of the "xorg.conf" is a dead end... it doesn't work... but the second weblink he has given us WORKS!!!

So, in order to use your mouse with acceptable speeds in Ubuntu 9.04 (or Fedora 11) just create a file by this command:
[B]
$sudo gedit /etc/hal/fdi/policy/10-x11-input.fdi[/B]

and inside that file paste the following code:

[B]<match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_options.AdaptiveDeceleration" type="string">7</merge>
</match>[/B]

Note that the number "7" is what works for me.
If you want a faster mouse use "3", for example.
If you want an even slower mouse use "10", for example.

Thanks for the great solution! I have a Razer Diamondback 3G. I sincerely hope the xorg.conf will change to the fdi files in the next release of Ubuntu, or perhaps in a Jaunty update. You really do not want your users to search around the web and configure files for hours for something as stupid and unnecessary as this.

---

### Post by Ubunthree on 2009-05-21
> **jmtdstoc said:**
> babuz' has given us the solution for this problem!!!

The use of the "xorg.conf" is a dead end... it doesn't work... but the second weblink he has given us WORKS!!!

So, in order to use your mouse with acceptable speeds in Ubuntu 9.04 (or Fedora 11) just create a file by this command:
[B]
$sudo gedit /etc/hal/fdi/policy/10-x11-input.fdi[/B]

and inside that file paste the following code:

[B]<match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_options.AdaptiveDeceleration" type="string">7</merge>
</match>[/B]

Note that the number "7" is what works for me.
If you want a faster mouse use "3", for example.
If you want an even slower mouse use "10", for example.

Ok, that seems to have done something, finally. I will experiment with different values.

I'm still not very clear on the differences between Adaptive and Constant, and so on; getting much out of the X.Org Wiki requires a deeper understanding of what's going on there than I have. Anyway, at least my mouse is actually usable now. Thanks!

---

### Post by Ubunthree on 2009-05-21
Hmmm... I may have spoken too soon. After mousing around for a few minutes, I'm understanding why this still seems a bit odd. This technique seems to put a maximum-speed limit on the cursor, regardless of how fast the mouse is physically moving. 

What I mean: If I move the mouse slowly, it needs about 2.5 inches to get the cursor from one side of the screen to the other. If I swipe the mouse quickly, it will crash into my scanner after about 6 inches, and the cursor will be barely a third of the way across the screen at the most. If I really jerk the mouse wildly, the cursor may end up only a couple of hundred pixels away from where it started.

What I need is this: Mouse moves fast, cursor moves fast. Mouse moves slow, cursor moves slow. If the mouse/cursor speed relationship is going to vary, it needs to be the opposite of this; slow mouse speed should yield higher precision of the cursor position.

Any advice on how to achieve this will be appreciated. Thanks again for the help so far, which has improved things at least...

---

### Post by jmtdstoc on 2009-05-22
I'm sorry I am not able to help anymore.
My Linux knowledge is very limited and I was just lucky in finding the link provided by bazuz'.

Let's hope some future update to Gnome solves this problem and returns to like it was until Ubuntu 8.10.

---

### Post by spacemonster on 2009-05-22
> **Ubunthree said:**
> Hmmm... I may have spoken too soon. After mousing around for a few minutes, I'm understanding why this still seems a bit odd. This technique seems to put a maximum-speed limit on the cursor, regardless of how fast the mouse is physically moving. 

What I mean: If I move the mouse slowly, it needs about 2.5 inches to get the cursor from one side of the screen to the other. If I swipe the mouse quickly, it will crash into my scanner after about 6 inches, and the cursor will be barely a third of the way across the screen at the most. If I really jerk the mouse wildly, the cursor may end up only a couple of hundred pixels away from where it started.

What I need is this: Mouse moves fast, cursor moves fast. Mouse moves slow, cursor moves slow. If the mouse/cursor speed relationship is going to vary, it needs to be the opposite of this; slow mouse speed should yield higher precision of the cursor position.

Any advice on how to achieve this will be appreciated. Thanks again for the help so far, which has improved things at least...

I had the same problem, after you've set up the fdi files, you can use the gnome mouse configuration tool in System - Preferences. Simply drag the mouse acceleration slider all the way to the bottom (or use xset 1 1 in a terminal).

---

### Post by Ubunthree on 2009-05-22
> **jmtdstoc said:**
> I'm sorry I am not able to help anymore.
My Linux knowledge is very limited and I was just lucky in finding the link provided by bazuz'.

Let's hope some future update to Gnome solves this problem and returns to like it was until Ubuntu 8.10.

Actually you did help; the mouse is much more usable now than it was before.

And I hope so too!

> **spacemonster said:**
> I had the same problem, after you've set up the fdi files, you can use the gnome mouse configuration tool in System - Preferences. Simply drag the mouse acceleration slider all the way to the bottom (or use xset 1 1 in a terminal).

I did that; it doesn't fix the issue though.

[COLOR="DarkRed"]xset m 1 1[/COLOR] resets the cursor speed to much too fast for my mouse. I have to use something like [COLOR="DarkRed"][COLOR="DarkRed"]xset m 1/6 1[/COLOR][/COLOR] to get the thing slow enough for delicate work, and then of course I have to sweep/lift/drop/sweep to move longer distances, because moving the mouse faster just slows the cursor down even more. I can *use* the mouse as it is, but really would like to fix this.

(edit) And before I did the .fdi file thing, xset wouldn't recognize a fractional acceleration value like that. It's getting too complicated for me to follow which adjustments are affecting which other ones...

---

### Post by lyall on 2009-05-29
thanks spacemonster

I have a IBM T23 laptop that the trackpointer was very slow and jumpy
I also use a usb mouse it acted the same.

after doing your instructions it works like is should.

Thanks again

---

### Post by lyall on 2009-05-29
thanks jmtdstoc

I have a IBM T23 laptop that the trackpointer was very slow and jumpy
I also use a usb mouse it acted the same.

after doing your instructions it works like is should.

Thanks again

---

### Post by Tamale on 2009-10-30
Can we please get a fix for this in 9.10 that doesn't involve command-line annoyances?

I just installed 9.10 and have a razer diamondback, and it's WAY too sensitive, even after moving both the acceleration and sensitivity sliders all the way down.. common people!

---

### Post by Ian Sinclair on 2010-05-26
Using 9.04, and the /etc/X11/xorg.conf files has no mention of mouse controls, deals only with video drivers. Using Kensington Optical Trackball and settings in Preferences - Mouse have no effect. Could I run the Kensington driver disc using WINE?

---

### Post by Tamale on 2010-09-29
> **Tamale said:**
> Can we please get a fix for this in 9.10 that doesn't involve command-line annoyances?

I just installed 9.10 and have a razer diamondback, and it's WAY too sensitive, even after moving both the acceleration and sensitivity sliders all the way down.. common people!

this is at least a little easier:
[http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/)

Open a terminal
Run the command: xinput --list --short
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Razer USA, Ltd DeathAdder Mouse         	id=6	[slave  pointer  (2)]
&#9116;   &#8627; Razer USA, Ltd DeathAdder Mouse         	id=7	[slave  pointer  (2)]
&#9116;   &#8627; Razer DeathAdder                        	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                  	id=10	[slave  keyboard (3)]
Note the name of your device. In my case, manipulating ‘Razer DeathAdder’ worked.
Set the constant deceleration for the device:
xinput --set-prop "Razer DeathAdder" "Device Accel Constant Deceleration" 5
That’s it. You might have to play around with the value, but 5 slowed down my mouse sufficiently.

To see the current settings for the device:
xinput --list-props "Razer DeathAdder"
To turn off mouse acceleration:
xinput --set-prop "Razer DeathAdder" "Device Accel Velocity Scaling" 1
To perform the tuning automatically, I simply created a file containing the script below, ran chmod +x on it and added it to System -> Preferences -> Startup Applications in GNOME:

#!/bin/sh
xinput --set-prop "Razer DeathAdder" "Device Accel Constant Deceleration" 5
xinput --set-prop "Razer DeathAdder" "Device Accel Velocity Scaling" 1

---

### Post by humina on 2010-12-01
Thank you tamale, that did it for me!  Just got a new mouse and it was unusable before.

I think a more permanent solution is to have some sort of custom udev configuration (or better yet a gui control for this setting somewhere).  Until then I'm just going to use a startup script.

---

### Post by cosmic_cow on 2012-11-19
Automagical id grab variation to be used as a startup script:

```

#!/bin/sh

mouse=` xinput | grep DeathAdder | awk '{print $6}' | awk 'BEGIN {FS="=";} {print $2}'`
xinput --set-prop $mouse "Device Accel Constant Deceleration" 5
xinput --set-prop $mouse "Device Accel Velocity Scaling" 1

```

---

### Post by wildmanne39 on 2012-11-19
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

