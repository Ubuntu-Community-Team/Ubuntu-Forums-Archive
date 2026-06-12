---
title: "Newbie trying to change screen resolution in natty"
date: 2011-10-04
forum: Hardware
---

### Post by unwsp on 2011-10-04
I recently installed 11.04 on an older model desktop, which uses a monitor with a 1280x1024 native resolution.  Ubuntu failed to correctly detect this, and instead only allows a 1024x768 resolution.  I would like to remedy this.

After some searching around, I discovered that the config file I should be using to tweak monitor/screen resolution settings is /usr/share/X11/xorg.conf.d/10-monitor.conf.  The file did not exist, so I created one.  Based on various posts I've found online (and my monitor specs), I put the following text in the file:

```

Section "Monitor"
       Identifier      "Monitor0"
       HorizSync       31 - 80
       VertRefresh     56 - 75
EndSection

Section "Device"
       Identifier      "Device0"
       Driver          "intel"
EndSection

Section "Screen"
       Identifier      "Screen0"
       Device          "Device0"
       Monitor         "Monitor0"
       DefaultDepth    24
       SubSection      "Display"
               Depth   24
               Modes   "1280x1024"
       EndSubSection
EndSection

```

None of the discussions I'd read online said anything about how to apply these changes, so I just rebooted.  The monitor is still at 1024x768, and still does not list any higher resolutions as available.  What do I need to do now?

---

### Post by unwsp on 2011-10-06
Still haven't figured out how to make this work.  Any help would be greatly appreciated.

---

### Post by fantab on 2011-10-10
> **unwsp said:**
> I recently installed 11.04 on an older model desktop, which uses a monitor with a 1280x1024 native resolution.  Ubuntu failed to correctly detect this, and instead only allows a 1024x768 resolution.  I would like to remedy this.


I too have the exact problem... my other desktop uses **AOC LM725 Monitor with 1280x1024 native resolution**... however **I cannot get any more than 1024x768 resolution**. It is very annoying.

Any help will be appreciated.
Thanks.

---

### Post by snafu006 on 2011-10-10
Are they old CRT screens? if they are then just press the buttons on the monitor and resize it.

---

### Post by fantab on 2011-10-11
> **snafu006 said:**
> Are they old CRT screens? if they are then just press the buttons on the monitor and resize it.

Mine is 2-4 years old LCD TFT, I had bought it used.... [*image link*]("http://pricespy.co.nz/product.php?p=33147")

---

### Post by fantab on 2011-10-11
> **unwsp said:**
> I recently installed 11.04 on an older model desktop, which uses a monitor with a 1280x1024 native resolution.  Ubuntu failed to correctly detect this, and instead only allows a 1024x768 resolution.  I would like to remedy this.


> **fantab said:**
> I too have the exact problem... my other desktop uses **AOC LM725 Monitor with 1280x1024 native resolution**... however **I cannot get any more than 1024x768 resolution**. It is very annoying.

I have found the [**SOLUTION HERE**]("http://forums.linuxmint.com/viewtopic.php?f=49&t=76085#p444558").

---

