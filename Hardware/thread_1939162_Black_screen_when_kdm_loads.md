---
title: "Black screen when kdm loads"
date: 2012-03-11
forum: Hardware
---

### Post by redxii on 2012-03-11
I am starting to lose patience. I am trying k/ubuntu after a really really long time and can't believe it is still having these same issues even on different hardware.

I am using Kubuntu 11.10 64-bit on a HP g6-1b79us notebook. It has integrated Intel HD 3000 graphics on a Intel Core i5-2410M (2nd Gen), it does not have switchable or dual graphics cards.

When kdm loads my monitor turns off, meaning the backlight is off too. It is not frozen, but I can't switch to any other terminal. Pressing the power button does a proper shutdown.

Here is what I have tried:

[LIST]
[*]nomodeset - it works but I am stuck with 1024x768. This is awful, the native res is 1366x768.
[*]i915.modeset=0 [xforcevesa] - still, stuck at 1024x768
[*]combinations of pci=noacpi, acpi=off, etc - while it works at the native resolution, it is unacceptable beyond troubleshooting because USB, power management, etc are disabled.
[*]xorg-edge PPA - no difference
[*]installing all available updates including Intel driver.
[*]I tried configuring X using 'sudo X -configure', however, it causes the screen to go blank (black but monitor is still on). It is trying to use the native resolution/mode when running this command.[/LIST]

I have Googled ad-*******-naseum without an acceptable resolution. Most 'solutions' usually involve using nomodeset. Most situations from the search usually are switchable graphics, nVidia cards, dual monitors or caused by upgrading; none of which apply to me and only have fixes for those particular situations. This is a fresh install, and also occurs on the live CD.

Here's a Xorg log [http://pastebin.com/nJh01nUi](http://pastebin.com/nJh01nUi)
lshw [http://pastebin.com/XNvRaGMw](http://pastebin.com/XNvRaGMw)

---

### Post by redxii on 2012-03-11
Appears I had to compile a new kernel, I used 3.2.9 with the generic config as a template.

Like I had to do before, but I was hoping to avoid it. These issues are a bad case for getting people off of Windows, if I had not even used Linux before I would have not put up with this.

---

