---
title: "Gutsy w/ Dell Inspiron 6000 screen resolution problem"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by lhansen on 2007-10-22
I recently upgraded from feisty to gutsy via the update manager.  Everything went very smoothly. One thing I was really looking forward to with Gutsy was the better capabilities with screen resolution and dual monitors. I have been trying for a long time to get my Samsung Syncmaster with 1680x1050 resolution to work properly as clone or extended desktop with no luck in feisty.

Here's the problem. Tried to setup the Samsung montior with the "Screens and Graphics" menu. Upon logging back in, Gutsy informed me I was now using low graphics mode, and I couldn't even get the original 1280x800 resolution working on my laptop monitor. After some fiddling, I was able to get gutsy to boot without going into low graphics mode, but I can't get the proper resolution for my laptop screen let alone the Samsung monitor.

I am using the Intel i810 driver with the i915 chipset. In the "Screens and Graphics" menu I selected Generic - LCD Monitor 1280x800, but I only get a maximum of 1024x768.

Any help?

---

### Post by red devil on 2007-10-22
Hi,
I'm at work at the moment so I can't go into too much detail, but what you need to do is apply the 915resolution patch to enable widescreen displays - it's a BIOS level patch which, if you follow the instructions elsewhere on this forum (it's not that hard to use) will enable you to select the proper widescreen resolution. This is a common problem with Linux systems and the Intel graphics chipsets.
Hope that helps and sorry I can;t be more detailed - the boss is coming!
Red Devil

---

### Post by lhansen on 2007-10-22
I definitely played with 915resolution trying to get this to work before I upgraded to gutsy. It looks like it is still installed because when I type
```
sudo apt-get install 915resolution
```

then I am told that the latest version is already installed. When I type

```
sudo 915resolution -l
```

then I see

```
Intel 800/900 Series VBIOS Hack : version 0.5.3

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 60 : 400x772, 8 bits/pixel
Mode 61 : 400x772, 16 bits/pixel
Mode 62 : 400x772, 32 bits/pixel
Mode 63 : 512x771, 8 bits/pixel
Mode 64 : 512x771, 16 bits/pixel
Mode 65 : 512x771, 32 bits/pixel
Mode 66 : 400x772, 8 bits/pixel
Mode 67 : 400x772, 16 bits/pixel
Mode 68 : 400x772, 32 bits/pixel

```

This looks different then the updated 915resolution file that I created before my upgrade to Gutsy (for example, I had included several 1680x1050 lines in there ala this post [http://ubuntuforums.org/showthread.php?t=451719](http://ubuntuforums.org/showthread.php?t=451719)), but keep in mind that I can't even get my original resolution (1280x800) to work, and it was working before I tried to get this external monitor to function properly.

---

### Post by red devil on 2007-10-23
Hi again,
Forgive me if you already know this, but the 915resolution patch only works for the duration of your session unless you load your settings (the mode you chose, the X and Y resolutions and the bits/pixels) in the file etc/defaults/915resolution.
I´m guessing here, but could it be that the Gutsy upgrade wiped or corrupted this file?
With the correct settings in there the patch should work on every reboot - it certainly does for me.
Hope that helps,
Red Devil

---

