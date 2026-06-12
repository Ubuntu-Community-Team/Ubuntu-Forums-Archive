---
title: "Mouse issues. MS Wireless Comfort Desktop 2.0"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by ahsm on 2006-01-06
I have the mouse and keyboard combo. The keyboard works fine, and mouse is just horrible. I have to wait over a button to click it, sometimes the mouse clicks random places by itself. I can't do anything. How can I resolve this issue? Thanks.

---

### Post by emuman on 2006-01-06
Check the protocol setting for your mouse in "/etc/X11/xorg.conf" and change it to "IMPS/2".

---

### Post by crhooker on 2006-01-08
[QUOTE=emuman]Check the protocol setting for your mouse in "/etc/X11/xorg.conf" and change it to "IMPS/2".[/QUOTE]

I have the same issue with my M$ wireless mouse and keyboard as above, keyboard works fine but not the mouse. It worked with the live cd test I did before the full install and now does not.

I checked my file as you suggest, and since I am a newbie I just want to be sure, my protocol line says ImPS2 and not IMPS2, are you saying I need to make that change? I would just go ahead and do it but if it hoses my mouse I am not yet ready for prime time with keyboard commands and controls.

thanks

carl

---

### Post by otetiani on 2006-01-08
I am in transition from Windows XP to Ubuntu (after many other attempts to find a distro I like) and I use the MS wireless comfort 2.0 set in Windows.  I have the same issues, keyboard works great, mouse works for a while then I have to delete the driver and re-install.

For the first few times I thought it was the position of the wireless hub, then I thought it was batteries (used a ton).  Finally I say it's junk and switched back to my wired stuff.

Anyone else use this specific wireless set that got it to work?

---

### Post by monomaniacpat on 2006-07-03
[QUOTE=emuman]Check the protocol setting for your mouse in "/etc/X11/xorg.conf" and change it to "IMPS/2".[/QUOTE]

I was just looking around for an answer to this and noticed others had ImPS/2 in their xorg files, so thought I'd change from my explorer entry. Does upper case make a difference?

---

### Post by krowe on 2008-04-14
I have everything on the mouse working except the horizontal scroll buttons (side to side with the wheel). Here is the relevant entry in my xorg.conf:
```
Section "InputDevice"
  Identifier "MSMouse"
  Driver "evdev"
  Option "Protocol" "evdev"
  Option "Dev Name" "Microsft Microsoft Wireless Optical Desktop&#65533; 2.20"
  Option "Dev Phys" "usb-0000:00:02.0-1/input0"
  Option "Device" "/dev/input/mouse0"
  Option "Buttons" "9"
  Option "ZAxisMapping" "4 5"
  Option "DialRelativeAxisButtons" "6 7"
EndSection
```

Now i'm trying to get all the extra buttons on the keyboard to work with little luck. I don't think "DialRelativeAxisButtons" does anything. I read somewhere that it was supposed to make side to side scrolling work but xev shows nothing being pressed when  use it.

---

