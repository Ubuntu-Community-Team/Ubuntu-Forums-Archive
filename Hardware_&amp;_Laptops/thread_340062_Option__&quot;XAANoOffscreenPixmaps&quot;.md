---
title: "Option  &quot;XAANoOffscreenPixmaps&quot;"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by mysticmarks on 2007-01-16
i have a radeon 9200 vid card.
i am trying to setup to run 3d desktops like beryl. I have followed the guid suggesting some aiglx options and have setup all aspects of this install. i have run into some issues.
The first is this command.
Option  "XAANoOffscreenPixmaps"
it seems to crash my video card.

i have this for output:

glxinfo | grep vendor
libGL warning: 3D driver claims to not support visual 0x4b
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

and also:

glxinfo | grep "direct rendering"
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

i dont understand this lig GL warning. HELP!

---

### Post by fvgm on 2007-01-20
hi 
i have ati 9250..

in your case, try to put this line in Device section

Option "AccelMethod" "XAA" 

with this, you will tell to xorg to use XAA to accelerate graphics.. perhaps solves...

---

