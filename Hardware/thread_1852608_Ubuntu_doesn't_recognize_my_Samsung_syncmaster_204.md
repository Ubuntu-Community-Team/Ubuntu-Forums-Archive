---
title: "Ubuntu doesn't recognize my Samsung syncmaster 204b"
date: 2011-09-30
forum: Hardware
---

### Post by ferulebezel on 2011-09-30
It hasn't bothered me for years but I decided that I would rather have it in a portrait aspect ratio and the dropdown menu for rotation has no options except for 'Normal'.  

I'm hoping if I can get it to recognize the monitor it will allow me to rotate it.

---

### Post by theyranos on 2011-09-30
Hey, I have that monitor! Odds are this has more to do with your graphics card, though.

If you have an nVidia card, you have to explicitly enable screen rotation in */etc/X11/xorg.conf* by adding 
**Option "RandRRotation" "on"** to the **Section "Device"** block.

Not sure if that works for other GPUs or not, but at least it should be something else you can google :)

---

### Post by ferulebezel on 2011-09-30
> **theyranos said:**
> Hey, I have that monitor! Odds are this has more to do with your graphics card, though.

If you have an nVidia card, you have to explicitly enable screen rotation in */etc/X11/xorg.conf* by adding 
**Option "RandRRotation" "on"** to the **Section "Device"** block.

Not sure if that works for other GPUs or not, but at least it should be something else you can google :)

I do have an nVidia card and it didn't work.  All it did was prevent the system from completing the boot process.  Fortunately I backed up xorg.conf and had a live CD handy.

I didn't see anything in the under System->Administration->NVIDIA X Server Settings that seemed relevant either.  The strange thing is that in that System->Preferences->Monitors can't identify it.

---

