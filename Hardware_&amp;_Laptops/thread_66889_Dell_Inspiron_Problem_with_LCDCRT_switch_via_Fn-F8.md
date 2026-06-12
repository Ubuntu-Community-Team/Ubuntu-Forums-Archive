---
title: "Dell Inspiron Problem with LCD/CRT switch via Fn-F8"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by moonchilde on 2005-09-18
Hello,

I recently installed Ubuntu on a Dell Inspiron 5100  and I am trying to get the <Fn> F8 LCD/CRT keyboard switch to work.  I really want the ability to have the video output go to either the CRT, the LCD, OR both.  Right now, it always goes to BOTH.

I have a radeon 7500 Mobile (stock for this machine).

I've tried
Option	    "XkbModel" "dell101"  #in the InputDevice for the keyboard

some video card setting I've tried;

Section "Device"
	Identifier  "ATI Radeon Mobility 7500 (M7 LW)"
	Driver      "radeon"
	Option     "MonitorLayout"    "LVDS, CRT"  # enables both at same time
#	Option     "MonitorLayout"    "CRT, LVDS"  # enables CRT but not the laptop screen
 
lsmod shows i8k loaded.

I've googled, searched the forums and asked on IRC.  Anyone know how to do this?

thanks.

---

### Post by moonchilde on 2005-09-28
Oh well.

Since no-one seems to know how to get this working I guess I'll be going back to Windows, where everything works properly.

Too bad...  I really wanted Linux to work on the Laptop but it's not there yet.

---

### Post by websavages on 2005-09-29
Have a look at the NVIDIA readme file, it contains settings for xorg to do with multiple displays. I managed to get the display to span two screens (laptop panel and lcd) each running at their native resolution

Cheers ws

---

### Post by moonchilde on 2005-09-29
Yes, that's pretty easy if you read the redeon man pages, but not exactly what I want to do,  I want to toggle between CRT<->LCD.  That is, via the Fn-F8 keyboard shortcut, have a single display on either the CRT/projector or the LCD, or both.

The Fn-F8 key shortcut has no effect on the display, which is the issue.

Thanks, though.

---

### Post by JLB on 2005-09-30
this works out of the box for me on my hp laptop using ubuntu breezy.

---

### Post by aanderson on 2005-09-30
Also works out of the box on my Dell Inspiron 2200 using Breezy

---

### Post by websavages on 2005-10-01
[QUOTE=moonchilde]
The Fn-F8 key shortcut has no effect on the display, which is the issue.
Thanks, though.[/QUOTE]

I know from the afore mentioned readme file, that if you add twinview directives to the xorg.conf file it will disable the fn+f8 button. perhaps ati does the same??

Cheers ws

---

