---
title: "Matrox Millennium II Display Problems"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by debian_ on 2005-06-05
Hi, I recently got an old Compaq Deskpro 6000 (Pentium 2 333mhz, put 224mb of ram in it) and installed Hoary on it. Everything seems to be fine except for an odd video abnormality I'm experiencing.

Under the mouse cursor, when I move it around, patches of blue vertical bars appear. Also, when I drag a window from side to side (horizontally) a yellow smear effect appears under where any text in the window was. The more I drag the deeper and larger the smear gets.

I've tried changing resolutions, color depth, refresh rates, etc to no prevail. I've tested on 2 different monitors and it happens on both. I checked in the Device Manager under System Administration, and it appears Ubuntu detects it fine. I attempted swapping the Matrox Millennium II out, and putting in an old ATi Rage Pro Turbo card, but it seems the computer doesn't like other graphics cards, and I get a BIOS beep when I attempt to power up using the ATi card (1 long beep, 2 short. I believe it signifies a display adapter error). 

Further evidense I believe of the display error is when I'm shutting down and it goes from graphic mode to console, theres a repeating pattern of miscelaneous characters every second space on the entire screen.

Sorry if my description is a little hard to understand. I'm relativly new to linux with only little experience in the past, so if in fact this is an error with X instead of my graphics card, I apologize for pasting in the wrong forum.

Any help would be greatly appreciated, thanks in advance.

---

### Post by voidlogic on 2005-06-11
In the x.org config, try changing the driver to VESA ("vesa"), obvously with that machine you were not planning on gamming anyway. If I recall correctly the Matrox Millennium II is fully VESA compatible (VESA v1.2? maybee 2.0). So give that a shot. If the driver is already VESA, try finding third linux drivers for the card. Hope that helps.

voidlogic

----------------------------------------
I need Help!! [http://www.ubuntuforums.org/showthread.php?t=39869&highlight=serial](http://www.ubuntuforums.org/showthread.php?t=39869&highlight=serial)
 ](*,)  ](*,)  ](*,)

---

