---
title: "Logitech MX510 button-mapping in Ubuntu 11.10, [kernel: 3.0.0-17-generic (64bit)]"
date: 2012-04-15
forum: Hardware
---

### Post by honklinux on 2012-04-15
Chances are this is working with other dated MX mice equally. 

Instructions if found regarding how to write up the Xmodmap were of no avail. Half the buttons were not working and couldn't be used. 

_**Disclaimer: I have no idea what I did, just succeded by very persevering "trial and error", odd thinking and serendipity.**_ Please don't laught, I was victimized by this!

The  main problem was that many buttons generated a "LeaveNotify" event when  pressed in "xev" and not the desired "Press" or "Release" events which could be used, owing  to faulty mapping.

Forget your mouse has so many buttons. Yes. Forget it.
Certainly not all steps and settings here will be necessary but I am too lazy and spent now to dissect which were reduntant, sorry.

As mentioned, I used xev to see which buttons give a LeaveNotify response.

_Setting up the mouse_:

1. Use xinput to see how many buttons on your mouse are recognised: 
> xinput --list 
xinput query-state "*id-numbe*r"             *####### eg. "6"*
[I]
My weird mouse was listed with 16 buttons, though it has only 10 , counting "mouse-wheelup and "mouse-wheeldown"[/I] *as separate buttons*. Funny driver.

2. Now, in order to edit the xorg.conf [in /etc/X11] 
-one needs device name
> cat /proc/bus/input/devices-figure out the input-path and event-number
> ls -al /dev/input/by-pathMy xorg.conf afterwards contained this:

> Section "Module"
  load "evdev"
EndSection

Section "ServerLayout"
...
    InputDevice    *"Logitech MX510"*  [I]### or any given name
[/I] ...
EndSection

Section "InputDevice"
    # generated from default
    Identifier     *"Logitech MX510"*
    Driver         **"evdev"**
    Option[B]         "Dev Name" "Logitech USB-PS/2 Optical Mouse"
[/B]     Option         "Dev Phys" "**usb-*/input0**"   *# I suggest * as a wild card*
    Option         "SendCoreEvents" "on"
    Option **        "Device" "/dev/input/event8"**   
    Option         "Buttons"       "**16"**
    Option         "ZAxisMapping"  "4 5"
    Option         "Emulate3Buttons"       "false"
EndSection
Which  event is standing for your mouse depends, in my case it was always  "mouse1" and that was mutually exchangeable with "event8". Please remember to backup the xorg.conf before changing it, troublesome entries can prevent X from starting and you'll have to reset.[INDENT]*I also disabled the file /etc/X11/Xsession.d/57xmodmap by renaming it for it was not helping.**I  should also mention limiting the "Buttons" to "10" will still give the  same xinput reports but will disallow values higher than 10 in the  Xmodmap to have an effect. God knows if this helped...*
[/INDENT]):PNow the fun part. [B]*Inexplicable but working.*
_The mapping._[/B]

3. Edit your
~./Xmodmap   [ 0 values deactivate buttons]

> pointer = 1 2 3 4 5 0 0 8 9 14 11 16 0 0 0 0 
Explanation: 
**For  some obscure programming-reason the apparent 10 buttons, an MX510 has  to offer, correspond to the positions  x x x x x 0 0 x x x x x 0 0 0 0**   in a .Xmodmap set up for 16 buttons. What is more, speaking for my  system, **only numbers [1,2,3,4,5,8,11,9,14,16] can be assigned to them** - the order is not important. 
Other  numbers in the range [1;16] -the range xinput suggested- as for instance the 7 or 12 can be  assigned to them BUT will NOT result in a "Button Press/Release" event  in xev, UNLESS another working button on that mouse gave a proper response  and is **being held pressed.** 
If this does not help with **other old mice**, try to figure out which positions in the Xmodmap can be given the numbers which do already work in xev. Try all possible numbers in the range in various combinations.

I know it makes limited sense, not  having insight into that evdev driver.** I hope my post will spare some the frustration I had with this**, or alternatives like changing the distro or worse: Buying a new mouse the Window's way.

---

