---
title: "ATI Mobility M3 TV Out"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by ecliptik on 2005-06-14
I have a Dell Inspiron 4000 with an ATI Mobility M3 card in it. Xorg is working just fine with 3d acceleration and all that goodness. I'm attempting to get the TV Out working though and haven't had any luck. I have tried the atitvout and gatos utility but no luck just yet. Here's my info:

lspci output
```

micheal@essence:~$ sudo lspci -vs 1:0.0
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 00b0
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        I/O ports at ec00 [size=256]
        Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [50] AGP version 2.0
        Capabilities: [5c] Power Management version 2

```

xorg.confg device section
```

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage Mobility M3 (AGP)"
        Driver          "ati"
        VideoRam 8192
        BusID           "PCI:1:0:0"
#      Option "UseFBDev" "true"
        Option "AGPMode" "2"
        Option "AGPFastWrite" "true"
        Option "EnableDepthMoves" "true"
        Option "EnablePageFlip" "true"
        Option "backingstore" "true"
        Option "RenderAccel" "true"
        Option "SWCursor"    "true"
        Option  "UseInternalAGPGART"    "false"
        Option  "TVOutput"      "NTSC" #gives option not supported in Xorg.log
EndSection

```

atitvout output
```

micheal@essence:/etc/X11$ sudo atitvout -f ntsc auto
Forcing Rage Mobility/Rage 3D Pro LT mode
VBE call failed.
Maybe this command is not supported by your graphics adapter?
Did your parameters (if you specified some) really make sense?
Please try all other available commands before complaining!

```

Does anyone know of any tricks on getting these ATI Mobility cards to output to the TV? Any help would be awesome, thanks.

---

### Post by Davor281 on 2005-06-14
Did you connect the TV to the TV out on laptop before you turned the laptop on?

ENjoY!

Davor.

---

### Post by ecliptik on 2005-06-14
actually.... no I didn't.... I thought the atitvout utility would give me a more encouraging message than "VBE call failed", I'll try it out when I get home tonite.

So would this mean that it is possible for these vid cards to work with tvout correctly?

---

### Post by ecliptik on 2005-06-15
After connecting the laptop to the TV and rebooting while it was turned on I still didn't have any luck getting atitvout to work. I did a 'atitvout -f detect' but it only said the CRT and LCD are active. It looks like this program just doesn't like my vid card, are there any other ways to get ATI cards to do TV out? Thanks.

---

### Post by Davor281 on 2005-06-15
Found this link, hope it helps:

[http://www.linuxquestions.org/questions/archive/25/2004/06/4/124232](http://www.linuxquestions.org/questions/archive/25/2004/06/4/124232)

ENjoY!

Davor

---

### Post by ArBaDaCarBa on 2005-06-29
I also have the same problem... the not so fun part is that atitvout worked perfectly fine some time ago on a Mandrake 9.2. It didn't work when I upgraded on 10.1 and it doesn't work in Hoary...
I think it might be a problem with using Xorg instead of XFree.

---

### Post by xx404 on 2005-10-20
I read somewhere that the atitvout utility doesn't work with Xorg. I had trouble with it in Hoary but I managed to get it to work by trying it from a shell.

Hold <Ctrl><Alt><F1> to toggle between X and a console (replace F1) with whatever console you want to use. Try atitvout from there and see if you have more luck. To get back to X hold <Ctrl><F7> (or try all the function keys until one works).

You can get mplayer to play full screen videos from a shell but that's a different project...

---

