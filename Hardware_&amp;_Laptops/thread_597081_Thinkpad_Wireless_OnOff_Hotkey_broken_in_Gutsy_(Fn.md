---
title: "Thinkpad Wireless On/Off Hotkey broken in Gutsy (Fn+F5)"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by Lil on 2007-10-30
Hiya,

I've been using Gutsy for a while now on my ThinkPad T40 and there are a number of glitches between it and Feisty which are just a pain in the rear. Sadly the inclusion of some features just about outweigh ditching Gutsy on it, such as screen hotplugging with xorg 7.3 and xrand 1.2. Plus the NTFS writing and updated printer subsystem are great. Compiz and the Screens and Graphics manager are not at all relevant to why I'm using Gutsy as I use neither.

I've searched Launchpad for such bugs but not found any recent ones and search for posts on here doesn't yield many answers so I've started digging. My wireless card is the dreaded Intel 2100B but it works better under Linux than it ever did under Windows (where it was useless.)

In a default Gutsy configuration, Fn + F5 which is the Thinkpad's wireless on/off hotkey does not work. In Feisty it worked, along with Fn + F7, and the Fn + Home/End for brightness also worked with an on screen display.

In Feisty all of these keys worked as you would expect.

I've since learnt that the new ATI driver (radeon) disables Fn+F7 due to issues with display corruption, so that makes sense. What is needed is a way to control this with xrandr in combination with ACPI. That's a matter for another day.

In trying to detect what was going on I have started to learn about the values I can poke into:

```
/proc/acpi/ibm/hotkey
```

So if I do:

```
echo enable,0xffff >/proc/acpi/ibm/hotkey
```

(Which is setting all the hotkey control bits on) it appears to all work then (excluding Fn+F7 which can be changed if you poke in 0x0) but the downside is you then lose the sound volume on screen display...

Basically Gutsy appears to have made a right dog's dinner of this as it worked fine before. Is a solution in the works, has anyone solved this properly? What is the main reason for the regression here?

The problem is I really like Gutsy but it's got quite a few regressions and it is pretty buggy quite a lot of systems that were fine on Feisty if we're honest.

Vicky

---

### Post by MountainX on 2008-02-17
I have a T61p running Gutsy and Fn+F5 doesn't work for me either.

---

### Post by eddyanm on 2008-02-24
I had the same problem with my new T61p (w/ bluetooth and 4965agn).  It turned out that the thinkpad-acpi.modprobe file (or ibm-acpi.modprobe; can't recall)in /etc/modprobe.d has the incorrect mask and the system firmware is not handling the hotkey like it used to (so nothing happens when you press the ones masked like Fn-F5)

Mine from a fresh install of Gutsy with the latest package upgrade as of 2/24/2008 contained:

> option thinkpad_acpi hotkey=enable,0xffff8f experimental=1

specifically if you change 8f to a bitmap (comes out to be 10001111), it masks Fn-F5 to F7.

I simply changed it to 0xffffff to enabled the 3 hot keys.  You can even do 0xffffffff to enable currently undefined hot keys.

Do a reboot to make it take effect or do

> echo enable,0xffffffff >/proc/acpi/ibm/hotkey

to make it happen right away.

You can find more details online by searching thinkpad-acpi or ibm-acpi.

Eddy

---

