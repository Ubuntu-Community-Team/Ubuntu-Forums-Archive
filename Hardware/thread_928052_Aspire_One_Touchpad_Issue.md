---
title: "Aspire One Touchpad Issue"
date: 2008-09-23
forum: Hardware
---

### Post by bionickid on 2008-09-23
installed ubuntu as shown in [https://help.ubuntu.com/]("https://help.ubuntu.com/community/AspireOne").
everything worked fine.
today I got problems with my touchpad.

cant left/right click anymore.

reinstalled ubuntu.

no leftclick is working most of the time.
an extern usb mouse is working fine. (UPDATE: wrong, is not solving the problem :( )
also tried: [http://falsepositive.eu/archives/20080829-schon-kaputtgespielt/42]("http://falsepositive.eu/archives/20080829-schon-kaputtgespielt/42")

is this a hardware problem?

---

### Post by Buffalo Soldier on 2008-10-16
I'm having the same problem. I can't believe it's just the two of us with this hardware issue. Or probably we're unlucky to have a broken hardware??? :(

---

### Post by teaker1s on 2008-10-29
strange running intrepid have no touchpad  issues
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

---

### Post by poldie on 2008-11-07
> **teaker1s said:**
> strange running intrepid have no touchpad  issues
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

My touchpad is completely dead after a clean 8.10 install.  I'm sure it worked under 8.4.1 until I did some mods to get wifi/audio working properly.

What's a good starting point to see if my touchpad is even visible to the OS?

---

### Post by thor2002ro on 2008-11-08
did you guys try adding to /etc/X11/xorg.conf

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "synaptics"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mouse0"
        Option      "ZAxisMapping" "4 5 6 7"
        Option      "CorePointer"
        Option      "HorizEdgeScroll" "1"
EndSection


i use this on my aspire one and works great. Hope it helps

---

### Post by poldie on 2008-11-12
> **thor2002ro said:**
> did you guys try adding to /etc/X11/xorg.conf

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "synaptics"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mouse0"
        Option      "ZAxisMapping" "4 5 6 7"
        Option      "CorePointer"
        Option      "HorizEdgeScroll" "1"
EndSection


i use this on my aspire one and works great. Hope it helps

Thanks, but this makes no difference - my touchpad is completely inactive.  I hope it's not broken!  Is there some way of checking if the hardware is visible to Ubuntu, and testing it at some low level (ie before drivers are active)...then try the drivers? Or something?

---

### Post by thor2002ro on 2008-11-12
try in terminal 
```
dmesg | grep Synaptics 
```

and 

```
dmesg | grep mouse 
```

and post results

there have been cases of the touchpad being bad .... did you try other os to confirm if its functional?

did you try the fn conbination ....? if i recall thers a fn combination to disable touchpad

Edit: Fn + F7

---

### Post by poldie on 2008-11-13
> **thor2002ro said:**
> try in terminal 
```
dmesg | grep Synaptics 
```

and 

```
dmesg | grep mouse 
```

and post results

there have been cases of the touchpad being bad .... did you try other os to confirm if its functional?

did you try the fn conbination ....? if i recall thers a fn combination to disable touchpad

Edit: Fn + F7

Thanks - I'll give that a go tonight.  In the meantime I'm posting this link:

[http://ubuntuforums.org/showthread.php?t=979865](http://ubuntuforums.org/showthread.php?t=979865)

to connect the two threads about this issue.


Edit:  The Fn + F7 'trick' worked!  Amusing.  Thanks for that.  I feel so stupid (but I'm used to them not working - I have to reboot for external monitors to work properly).

---

### Post by mikegi on 2009-02-19
"Fn + F7" worked for me. The answer was staring me in the face!!

---

### Post by BerndtheBread on 2009-03-16
Hi there...

Okay... I try to explain MY problem with the touchpad:

The left button doesn't work at all. It stops working after a while (about 30min working on my Aspire One).
Ah, and the touchpad itself makes strange things too. Only the click-by-touch works as a left-button (btw, the right button works properly), but only after a X-server restart ofter booting my Ubuntu 8.10 Intrepid. On the first start, the cursor marks everything as the left-button is allways pressed and the left button still doesn't work. By restarting the X the click-by-touch works... It drives my mad... especially since this all disapears when I don't start my Aspire One for about 24-30h. Than (for a while) everything (even the left button) works fine... and then... bang... left button and click-by-touch stops.... argh....

The short-key of STRG-F7 doesn't make a difference. Just turn the touchpad on and off keeping the problem.
The Script for the xorg.conf didn't work either...
xmodmap -pp points to the correct buttons and xinput lists te correct numbers too...

I have no idea what this is... maybe a bug in the synaptics driver?
PLEASE help me... I'm going crazy...

Thanks
BerndtheBread

---

### Post by wouter87 on 2009-03-19
I have exactly the same problem as berndthebread.
if anyone can solve it, please let me know!
thanks,
w

---

### Post by Teabicky on 2009-03-19
I had all sorts of problems with mine until I installed "easypeasy".  Its a version of 8.10 that some clever people have configured for notebooks.  Everything worked out of the box.

> [http://www.geteasypeasy.com](http://www.geteasypeasy.com)

---

### Post by ttflyer on 2009-04-09
> **BerndtheBread said:**
> Hi there...

Okay... I try to explain MY problem with the touchpad:

The left button doesn't work at all. It stops working after a while (about 30min working on my Aspire One).
Ah, and the touchpad itself makes strange things too. Only the click-by-touch works as a left-button (btw, the right button works properly), but only after a X-server restart ofter booting my Ubuntu 8.10 Intrepid. On the first start, the cursor marks everything as the left-button is allways pressed and the left button still doesn't work. By restarting the X the click-by-touch works... It drives my mad... especially since this all disapears when I don't start my Aspire One for about 24-30h. Than (for a while) everything (even the left button) works fine... and then... bang... left button and click-by-touch stops.... argh....

The short-key of STRG-F7 doesn't make a difference. Just turn the touchpad on and off keeping the problem.
The Script for the xorg.conf didn't work either...
xmodmap -pp points to the correct buttons and xinput lists te correct numbers too...

I have no idea what this is... maybe a bug in the synaptics driver?
PLEASE help me... I'm going crazy...

Thanks
BerndtheBread

This just happened to me.  When I booted into windows, I found (by looking at the synaptic animation on the taskbar) that the right mouse button was stuck "ON."  This is a known problem with the aspire one.  Mine is going back to the store (I don't know of a fix).

I hope that helps...

---

### Post by drvolk on 2009-04-21
I have the problem with "hanging left mouse" touchpad function, which disapears after restart of the x-server too.

I did not notice this problem with the gparted live usb distro.

I will try to check what is the difference to UNR here ...

---

### Post by Cardcaptor Stacey on 2009-06-01
I'm currently having this problem.

I found a "fix" from [http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/](http://ubuntu.wordpress.com/2006/03/24/disable-synaptics-touchpad/) which disables the touchpad completely but a USB still works great via /etc/X11/xorg.conf.

Here it is:
```
Section “InputDevice”
Identifier “Synaptics Touchpad”
Driver “synaptics”
Option “SendCoreEvents” “true”
Option “Device” “/dev/psaux”
Option “Protocol” “auto-dev”
Option “HorizScrollDelta” “0&#8243;
Option “SHMConfig” “on”
EndSection
```

I hope it all works for you. :)

---

### Post by maly.82 on 2009-06-23
Hi there,

    i had the same problem, couple minutes ago it occured again on my Acer Aspire One. It has all symptoms - Synaptic driver on windows shows that my left button is pushed in. Right button works but taping on touchpad does nothing. i even tried to take off battery and that didn't do anything. 

So here it is i've installed Ubuntu Network Remix and it was working fine yesterday - the day i've installed it - but now it's not. I've only updated it and add some extra programs.

Last time i've managed to solve this problem by simply doing nothing - put laptop on sleep and left it for a while.

Suddenly when battery get out of juice i connected it to recharger and boot up machine - since then my touchpad was working properly.


Hope that help You Guys - i'll update this post when i will run out of juice

---

### Post by justindisgustin on 2010-06-14
The fn + f7 trick fixed my issues.  I was having a problem loading gnome and trying to get into recovery mode, but I couldn't remember the key to do so (hold shift during startup), so I think what I did was hit every key on my keyboard in unison.  At which point the desktop loaded and I had lost mouse functionality.
I just chalked it up to more of the same issues I was already having til I read this thread hah

---

