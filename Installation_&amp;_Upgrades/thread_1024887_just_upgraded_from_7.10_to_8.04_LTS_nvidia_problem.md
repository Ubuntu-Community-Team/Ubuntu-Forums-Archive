---
title: "just upgraded from 7.10 to 8.04 LTS nvidia problems"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by unseenbeing on 2008-12-29
i just upgraded like the title says. when ever i boot up it says linux is running in low graphics mode. i only have 800x600 or the other smaller one (cant thing of what it is). i would like to have my old res back from when i was at 7.10.

what do i do to fix this

---

### Post by ajgreeny on 2008-12-29
What hardware are you running?  It sounds as if you need to enable a proprietary graphics driver, so try *System > Administration > Hardware drivers* and see if you can do it that way.

---

### Post by unseenbeing on 2008-12-29
i have done that already.. serveral times and different drivers.

from what it seems like is xorg is crashing at boot and loading graphics safe mode of some kind (after the little ubuntu loading bar i get text based that flashes and then  it says low graphics mode and gives me a choice of selected my stuff by hand)

---

### Post by waltkerr on 2008-12-29
After startup, run System - Administration - Hardware Drivers. It should identify the need for an Nvidia driver. If you let it go ahead and download it, it will give you a message that it is not open source software and may be a problem. They got that right! After the mandatory restart, it locks my system up at the login screen every time. I've tried this twice with fresh Ubuntu installs both times. I'm on my third install and I'll leave the system at the 800x600 resolution (best it can do), until I can do more research on this. Sorry this isn't a solution, only that others are having the same issue with Nvidia graphics.

---

### Post by ajgreeny on 2008-12-30
I think from memory that there is a problem with 8.10 not being compatible in some way with some of the older legacy nvidia drivers;  have a look in the 8.10 release notes for more info and to see if your card is affected.

---

### Post by unseenbeing on 2008-12-30
im not using 8.10 im using 8.04 lts

---

### Post by unseenbeing on 2008-12-30
ok i just fixed it.
not sure if this will fix others but it fixed mine


i reinstalled the nvidia-glx-new driver.
enabled it in the hardware drivers menu.
restarted like it asks.
but, i booted recovery mode and chose to fix xserver option
let it do its thing and then chose to boot normally.

and now im no longer dealing with the 800x600 low graphics crap.

i cannot however turn on desktop effects

---

