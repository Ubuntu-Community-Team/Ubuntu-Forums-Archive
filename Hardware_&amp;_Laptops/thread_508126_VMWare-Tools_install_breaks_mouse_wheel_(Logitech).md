---
title: "VMWare-Tools install breaks mouse wheel (Logitech)"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by ness0216 on 2007-07-23
After installing vmware-tools the scroll wheel on my logitech mouse no longer works. I've searched and tried a common fix of changing Protocol to ImPS/2 in my xorg.conf but to no avail. I was wondering if anyone else had this issue and found a solution. Here's my mouse info in xorg.conf. Btw before this my scroll wheel was working fine.

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

---

### Post by popch on 2007-07-24
I seem to have the same problem in a ubuntu (Feisty) guest running under an XP host. No wheel, otherwise OK. I have no solution.

---

### Post by nelio2k on 2007-08-08
After doing some googling, I found this link:

[http://www.tipstrs.com/tip/89/Enable-mouse-scroll-under-VMware-guest](http://www.tipstrs.com/tip/89/Enable-mouse-scroll-under-VMware-guest)

Which says:

In case where using guest Linux under VMware, mouse scroll does not work.
To fix this, open terminal and type the following:
$ sudo gedit /etc/X11/xorg.conf
Then find "InputDevice" section with Identifier "Configured Mouse"
Change Option "Protocol" "ps/2"
to
Option Option "Protocol" "IMPS/2"
Last restart X using Ctrl + Alt + Backspace

Hope this works for you. It worked for me.

---

### Post by lee555J5 on 2007-10-28
Great solution! It worked for me too.

WinXP Pro SP2 host
VMware 5.5.5
Ubuntu 7.10 guest
Microsoft IntelliMouse Explorer 3.0 USB

Lee

---

### Post by vek on 2007-12-21
This fixed it for me too, thank you.

---

### Post by breaking on 2008-02-14
Thanks, nelio2k.

---

### Post by Magicmat on 2008-04-01
I just found this thread through Google and the solution posted worked fine. However, I subsequently found a better solution: In your xorg.conf, in the mouse InputDevice section (the same section talked about with the earlier fix,) change the line
 [font=courier] Driver          "mouse"[/font] 
to 
[font=courier] Driver          "vmmouse"[/font]

Edit: And, of course, change back the protocol to "ps/2" if you previously changed it to "IMPS/2" because of the earlier suggestion in this thread.

With the IMPS/2 method, I noticed a lot of quirks such as "flickery" animated cursors, no catch/release support within the session launcher, and weirdness in full screen mode when the cursor tried to go near the top-center of the screen, where the VMWare control strip overlay resided. This fixes all of those problems and just seems to work better overall, while retaining mouse wheel support. Why VMware Tools doesn't do this in the first place, I have no idea.

Now if only I could get my forward/back buttons working . . .

---

### Post by Gigi33 on 2008-04-26
Wheter I use PS/2 or ImPS/2 made no difference for me.

Adding ```
	Option		"ZAxisMapping"	"4 5"
``` did the trick!

Working xorg.conf:```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection
```

WinXP Pro SP2 
VMWare Workstation ACE 6.0.2
Ubuntu Hardy
Logitech MouseMan Dual Optical

---

### Post by shornby on 2008-05-04
Hey,

I'm using Fusion 1.1.2 with Ubuntu 8.04, and could not scroll the mouse, even after compiling vmtools.

Speaking of vmware tools - after numerous attempts, I was able to compile VMware tools, using [this *excellent* link]("http://peterc.org/2008/62-how-to-install-vmware-tools-on-ubuntu-hardy-804-under-vmware-fusion.html").

But still no mouse scroll!

Adding the line:

	Option		"ZAxisMapping"	"4 5"

to xorg.conf made everything work perfectly.

Regards,

S

---

### Post by ricnmar on 2008-05-06
This worked for me too!  

I pasted in the lines:

Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"

Now I can SCROLL!!!

Thanks!

---

### Post by stefanadelbert on 2008-05-19
Worked for me too.

/etc/X11/xorg.conf:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "vmmouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
EndSection

Host: WinXP SP3
Guest: Ubuntu 8.04
VMWare: Player 2.03 (build 80004)
Mouse: Logitech Wheel Mouse

---

### Post by rarsa on 2008-05-22
I had already tried the zaxismapping as the "obvious" solution. Adding the IMPS/2 did the trick and the vmmouse was the icing in the cake.

So this is the winning combination.

Thank you.

---

### Post by Cybie257 on 2008-06-01
> **Gigi33 said:**
> Wheter I use PS/2 or ImPS/2 made no difference for me.

Adding ```
	Option		"ZAxisMapping"	"4 5"
``` did the trick!

Working xorg.conf:```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection
```

WinXP Pro SP2 
VMWare Workstation ACE 6.0.2
Ubuntu Hardy
Logitech MouseMan Dual Optical

Never tried to 'add' the Protocol, as it never existed in my conf file, but added the ZAxisMapping. Worked Great!! Thanks!

Win XP SP3, VM Workstation 6.0, vmtools, Ubuntu 8.04.
soon to be Ubuntu 8.04 with Win XP Virtual. :)
Oh, and if matters, Logitech USB Scroll Mouse.

-Cybie:guitar:

---

### Post by Catsworth on 2008-06-06
> **Gigi33 said:**
> Wheter I use PS/2 or ImPS/2 made no difference for me.

Adding ```
	Option		"ZAxisMapping"	"4 5"
``` did the trick!

Working xorg.conf:```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection
```

WinXP Pro SP2 
VMWare Workstation ACE 6.0.2
Ubuntu Hardy
Logitech MouseMan Dual Optical


Bloomin' marvelous.

This worked a treat on my lappy which was having the same problem with a Microsoft Intellimouse.

---

### Post by Schalken on 2008-06-24
Just the "ZAxisMapping" option was needed to enable the scrollwheel on my external mouse. However, nothing seems to enable scrolling with my laptop's touchpad (Dell/Synaptic).

Has anybody got scrolling the the VM to work with their touchpad?

---

