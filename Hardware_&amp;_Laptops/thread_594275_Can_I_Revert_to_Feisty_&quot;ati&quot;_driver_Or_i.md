---
title: "Can I Revert to Feisty &quot;ati&quot; driver? Or is there better than &quot;vesa&quot;?"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by OzzyFrank on 2007-10-27
Hi. I'm one of those unfortunate souls who lost even more ATI graphics card functionality with the upgrade to Gutsy. In order to get a working display, ie not totally garbled using the pretty basic "ati" driver, I have had to resort to using the even more basic "vesa" driver. It was one thing not being able to use "fglrx" or even the "radeon" driver in Feisty... but not being able to use the most basic features of "ati" is really a major disappointment. Why? Coz I can't even watch vids or DVDs without choppy playback, especially if I try to expand the size or (god forbid) watch in fullscreen. And of course I can't get all the resolutions supported. So is there a way to get the ATI driver back the way it was in Feisty? Or is there at least something better than "vesa" (which is, I assume, the rason for choppy playback and limited resolutions)? Thanks

---

### Post by trippinnik on 2007-10-28
Don't know.  I'm not able to use the ati or radeon driver either, because if I do then I can't use sleep on my laptop.  It seems strange that hardware drivers would have such a big regression.  I'm thinking about going back to fiesty or switching.  I think it affects all the new releases of distros though, but I can't seem to find too much info on the ATI or Radeon open source driver.

---

### Post by cow_racer on 2007-10-28
> **OzzyFrank said:**
> Hi. I'm one of those unfortunate souls who lost even more ATI graphics card functionality with the upgrade to Gutsy. In order to get a working display, ie not totally garbled using the pretty basic "ati" driver, I have had to resort to using the even more basic "vesa" driver. It was one thing not being able to use "fglrx" or even the "radeon" driver in Feisty... but not being able to use the most basic features of "ati" is really a major disappointment. Why? Coz I can't even watch vids or DVDs without choppy playback, especially if I try to expand the size or (god forbid) watch in fullscreen. And of course I can't get all the resolutions supported. So is there a way to get the ATI driver back the way it was in Feisty? Or is there at least something better than "vesa" (which is, I assume, the rason for choppy playback and limited resolutions)? Thanks

I have an ATI x1400.  fglrx works fine.  Can't suspend the laptop tnough.

---

### Post by OzzyFrank on 2007-10-31
So anyone with an answer? (If you have an ATI card and all works fine, then you don't need to post here... unless it broke with Gutsy and you reverted back to the Fesity driver and that's the only reason it works).

---

### Post by daschmidty on 2007-11-01
I am having this same problem on my thinkpad x24. It uses the ati/radeon driver and now in gutsy, suspend is dead...apparently the driver is no longer supported or something like that...and on a P3 vesa is really not an option....the computer is slow enough as it is without needing any extra load on the cpu from video.

---

### Post by elamericano on 2007-11-02
Hey, it's working fine for me.... Ha just kidding ;-) I've had bad luck recently with people who comment without trying to be helpful. I feel your pain.

If I'm reading the end of this thread correctly:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

Then the new kernel will not run the old driver without a recompile. It also suggests trying the newest fglrx, but that didn't fix anything for me. I went back to the default ati driver, and sleep works again. I can't really get by without it.

T42/Mobility Radeon 9600 M10

---

### Post by daschmidty on 2007-11-02
This is not a problem with fglrx. On older thinkpads, apparently the driver is deprecated for the ati M6 series video cards. These cards are not supported by fglrx, as they are too old. They have instead always been supported by the open-source "ati" and "radeon" drivers. These however...seem to no longer work properly on this hardware either anymore as of the new Gutsy kernel. The only hope really is that someone patches the driver to be compatible with the new kernel.

---

### Post by OzzyFrank on 2007-11-06
So there's no way to get back "ati" that works for me, just the new "ati" that garbles the screen? So I'm really stuck with "vesa" for the duration of using Ubuntu??? Come on guys... someone MUST know some way to get around this. I just want back the crummy "ati" driver that at least gave me my choice of resolutions and let me watch vid clips and DVDs in fullscreen without going all choppy.

---

### Post by elamericano on 2007-11-06
Have you truly exhausted the graphic driver configurations available? You could experiment with the new graphic configurator from System->Administration->Screens and Graphics. If you pick something that doesn't work, it should revert back to your previous settings. You can try Radeon (fbdev) if you haven't tried that yet. Look at your options again. I've never had an ATI card that would only run with VESA.

---

### Post by OzzyFrank on 2007-11-06
System->Administration->Screens and Graphics doesn't even exist on my Gutsy-upgraded-from-Feisty system. So would be hard to use that, hehe. But I've changed it to that by editing xorg.conf, so will see what happens with the next reboot. And I have seen PLENTY of mention from others saying only "vesa" now works with their ATI card. It's a major problem. I think Ubuntu are trying to help boost nVidia sales, hehehe!

---

### Post by OzzyFrank on 2007-11-07
Nope... "fbdev" just gives me a black screen with a flashing underscore in the top left corner. Can't even get to a command prompt after that so have to reboot into recovery mode. Tried a couple more and same result. Even in Feisty the only one that ever worked for me was "ati" (there used to be a "radeon" and that never worked then either). Try any other new distro and it's fine. Sabayon I can even start desktop acceleration for Compiz-Fusion. In Feisty the only way I could run Beryl while using the "ati" driver was with a script... now with Gutsy I'm reduced to "vesa" with 4 available resolutions and choppy video playback, hehe. Gotta love progress!

---

