---
title: "Screen Rotation, NVIDIA drivers, slowness (Inspiron 8600/Geforce 5200)"
date: 2010-03-13
forum: Hardware
---

### Post by palmsey on 2010-03-13
I have an Inspiron 8600 mounted upside down under my kitchen cabinets. 

[IMG]http://farm4.static.flickr.com/3632/3633702619_7d5c104890.jpg[/IMG]

I had been running the Win 7 RC on it with the screen inverted, but the RC expired, so I put Ubuntu 9.10 on it. In the desktop settings, the rotation drop down just says "Normal" and doesn't give me an option to rotate the screen. I thought it might be due to my video drivers, so I downloaded and installed the latest Linux drivers for my card, a Geforce FX (Go?) 5200. When I rebooted with the nvidia drivers running, everything was super slow. I can see the screen refresh, windows take a few seconds to open, and Terminal never really finishes loading (it opens, but I don't see the cursor and I can't type anything) so I haven't been able to try xrandr with the nvidia drivers running.

I've tried putting all sorts of things into my xorg.conf file that I've seen recommended, stuff like:

Option "RandRRoation" "on" (or "true" - also tried with "RandRoatation" "RandRRotate" "RandRotate" etc)
Option "Rotate" "INVERT" (and other variations)

... but I can't get the screen to rotate. When I change the config file to not use the nvidia drivers anymore, things speed up, but I still can't rotate the screen. 

Doing all of this upside down is not fun. Help!

---

### Post by gordintoronto on 2010-03-13
I've searched and searched, and have not found any setting which will make the screen display upside-down. The "man xrandr" command displays options which are said to invert the screen, but they don't do it with my nVidia 9400GT card.

---

### Post by AaronP_ on 2010-03-16
> **palmsey said:**
> Option "RandRRoation" "on" (or "true" - also tried with "RandRoatation" "RandRRotate" "RandRotate" etc)
The option is "RandRRotation".  To invert the screen once that option is properly enabled, it's "xrandr -o inverted" (or use the graphical menu).

---

### Post by gordintoronto on 2010-03-16
> **AaronP_ said:**
> The option is "RandRRotation".  To invert the screen once that option is properly enabled, it's "xrandr -o inverted" (or use the graphical menu).

I added:
	Option  "RandRRotation" "True"
in the ServerFlags section, rebooted, then in Terminal typed:
xrandr -o inverted
 
And got:
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

I found nothing relevant in the NVIDIA X Server Settings GUI.

---

### Post by AaronP_ on 2010-03-17
See the README: [ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.15/README/xconfigoptions.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.15/README/xconfigoptions.html)

[quote=README]
The following driver options are supported by the NVIDIA X driver. They may be specified either in the **Screen or Device** sections of the X config file.
[/quote]

---

### Post by gordintoronto on 2010-03-17
> **AaronP_ said:**
> See the README: [ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.15/README/xconfigoptions.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/195.36.15/README/xconfigoptions.html)

Thanks!

I plan to include this in a future Q&A column of Full Circle Magazine, probably the May issue.  If you want to send me a private message, I will credit you by name, otherwise I will credit your screen name.

---

### Post by AaronP_ on 2010-03-17
> **gordintoronto said:**
> Thanks!

I plan to include this in a future Q&A column of Full Circle Magazine, probably the May issue.  If you want to send me a private message, I will credit you by name, otherwise I will credit your screen name.
That's okay, no credit necessary.

---

