---
title: "installation hangs at beginning"
date: 2004-10-18
forum: Installation &amp; Upgrades
---

### Post by crun on 2004-10-18
Hello everyone

I've been using the live-cd version of Ubuntu and want to install it to HD. However, after selecting the preferred language (second option after booting)  the install just sits there (where it should start detecting hardware).

I've had the same problem with the Debian beta installer (but only using the 2.6 kernel, ther 2.4 installs fine). I've tried different boot options, like noscsi, but it all results in the same problem.

My hardware specs:
AMD Athlon XP 2700+
Asus A7N8X motherboard
Plextor DVD and Plextor CD writer

Does anyone have an answer to this? I've searched the forum and Googled around, but can't find any mention of it. Thanks very much.

---

### Post by FLeiXiuS on 2004-10-18
Are you installing from the live cd or the Warty ISO?

---

### Post by crun on 2004-10-18
I'm now trying to install from the Warty ISO, could installing from the live cd make a difference?

---

### Post by FLeiXiuS on 2004-10-19
Possibly, but what stage is the ISO in when its 'stuck'

---

### Post by crun on 2004-10-19
It's after "choose your location"

So in the startup process, you first get the boot prompt, then "choose a langauge", then "choose a location".

After that it should ask for your keyboard layout (I've tried the same Warty CD on a different machine and it works there) but instead the screen stays blank - no errors, just no activity anymore.

My keyboard is an USB Logitech Internet Navigator. I'll try to use a different keyboard to see if it makes any difference.

---

### Post by FLeiXiuS on 2004-10-19
Hmm...could possibly be a bad cd rom drive?  Or the processor over heats and freezes at the location point.  I would test the cd-rom drive just to be safe.  Does your PC make any particular types of noises?

---

### Post by crun on 2004-10-19
I think I've figured it out. I had my USB keyboard plugged into the PS2 port with a little extension-gizmo, so I unplugged it and put it in the USB port, and now the booting process seems to work fine. Weird.

Thanks for the suggestions FLeiXiuS. I'll post back when I've finished installing.

---

### Post by crun on 2004-10-19
Yes, installation went smoothly. Everything is running fine now.

---

### Post by spiraloid on 2004-10-19
I'm having the same problem with a nearly identical hardware setup:

Athlon XP 2100+
ASUS A7N8X
Pioneer DVD-RW

The debug screen says that USB module loading fails (specifically USB-hid and another one).. however, my keyboard is not USB. I do have a scanner, a printer, a mouse, and two gamepads connected to my USB ports, though. I'll try unplugging those and report back.

Could it be a problem with the nForce2 chipset?

I'm installing from the Warty ISO. If this doesn't work, I will give the LiveCD a spin.

**Update**: Installed and running beautifully. It appears the problem was either my Microsoft Sidewinder gamepad or my Logitech Wingman XTreme 3D joystick, as unplugging both of these worked. I haven't tested to see which specifically was the problem. Also, they were plugged into my front USB which might have something to do with it.

---

### Post by crun on 2004-10-20
It could have something to with the nForce chipset as we do have the same A7N8X motherboard.

---

### Post by FLeiXiuS on 2004-10-23
I'm glad to see you fixed your problem, ubuntu and xfree always had a problem finding my devices...for example (mice)  

Have fun with Ubuntu! :wink:

---

### Post by dorris on 2004-11-06
Bump
Is there no alternative for usb keyboard users, other than, USE a ps2, I would really like to resolve this issue and pull out me trusty usb keyboard, this one suxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx, oops, damn sticky keys.

---

### Post by beerorkid on 2005-03-14
I was having the exact same issue, it would freeze up right after I choose my language.  It was my logitech flightstick wingman.  It did install correctly with a 64bit install while the flightstick was plugged in.  In the 32bit install it gave me issues.

---

