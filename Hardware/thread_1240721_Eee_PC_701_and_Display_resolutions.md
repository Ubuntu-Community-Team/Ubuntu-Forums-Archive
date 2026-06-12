---
title: "Eee PC 701 and Display resolutions"
date: 2009-08-15
forum: Hardware
---

### Post by DavidFromCanada on 2009-08-15
I have a problem with my display options.
When I go to the display preferences on my Eee PC 701 I get only one resolution, 800x480.

I just installed a fresh Jaunty install from an old Intrepid install. On intrepid I had a lot of video options, everything down from 800x480. Now the issue is when I try to play a game at 640x480, it can't change the screen resolution. It just places it in a crappy way on the screen.

As an example with Half-Life:
```
Failed to initialize GEM.  Falling back to classic.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f4fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f518,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x16 @0! (XRandR)

```

Now I remember editing xorg to add video modes vaguely but when I add the modes to xorg the way I read how, I still don't get options for more resolutions in the display prefs. I can't install the array.org eeepc kernel because they're quite unstable in jaunty and I spent 2 hours solving the issue (install kernel 2.6.30).

---

### Post by DavidFromCanada on 2009-08-16
Bump

---

