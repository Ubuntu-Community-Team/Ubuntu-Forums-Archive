---
title: "Gnome boot hangs on Compaq V2000"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by IronKnuckles on 2005-08-14
Hello, it's me again... Having more problems with Ubuntu on my Compaq V2000 notebook.
ACPI appears to be working fine, and the IPW2200 wireless connection works fine. The problem is that when I boot up, Gnome hangs for a looong time. At least five minutes. At first I suspected that the IPW2200 was still connecting and that may be causing the lag, but switching to another terminal, I've discovered I can go into Lynx and browse.. So that's not the problem. It seems to be entirely a Gnome problem. Can anyone help me?

---

### Post by IronKnuckles on 2005-08-15
UPDATE:
Okay, I went on a hunch and tried to install the newer driver for the IPW2200. I followed the directions on the thread on the Ubuntu forums (search for IPW2200, HOWTO). I was hoping the newer firmware would have resolved this issue. Nope.
 ](*,) 
It still takes 5 or 6 minutes for me to load Gnome or go into sleep mode/ suspend-to-RAM from Gnome.
I know this lag is caused by the IPW2200 because I tried removing the old version first and there was no lag while it was uninstalled. When I installed it again, the lag returned.
Is this a known issue or should I file a bug report? And if so, where?

---

### Post by jamesrw on 2005-08-20
hey ive got the same notebook cept its the v2000z with the turion chip. I am using an ATI gfx card and was able to fix my boot hang by editng the xorg.conf. changes include:

comment out following in section 'module':
#	Load	"dri"

add the following in section 'device':
        Option          "NoAccel" "true"
        Option          "RenderAccel" "false"
        Option          "MergedFB" "off"

---

### Post by trash on 2005-09-19
[QUOTE=jamesrw]hey ive got the same notebook cept its the v2000z with the turion chip. I am using an ATI gfx card and was able to fix my boot hang by editng the xorg.conf. changes include:

comment out following in section 'module':
#	Load	"dri"

add the following in section 'device':
        Option          "NoAccel" "true"
        Option          "RenderAccel" "false"
        Option          "MergedFB" "off"[/QUOTE]


Worked like a charm on a buddies presario v2000, thanks jamesrw!

---

### Post by kozimodo on 2005-10-30
Any other issues with installing Breezy on the v2000z?  I'm considering buying one -- it's not exactly what I want but pretty close.

A related question: anyone know if there are any not too expensive laptops in the works with the Turion MT line of processors?  The Fujitsu s2110 does but it only comes with the 1.6Ghz, 512K L2 processor -- if it came with even a 1M L2 cache, I'd probably go that route.

---

