---
title: "Wacom CTH-480 works with 14.04 but Settings/Wacom Tablet shows &quot;No tablet detected&quot;"
date: 2015-12-22
forum: Hardware
---

### Post by anton-tagunov on 2015-12-22
Hi

Wacom CTH-480 (Intuos4 series)
Ubuntu 14.04
3.19.0-42 kernel

the tablet works!!!
but when I launch Settings/Wacom Tablet I see

"No tablet detected"

interestingly xsetwacom --list devices prints

Wacom Intuos PT S Pen stylus        id: 9    type: STYLUS    
Wacom Intuos PT S Finger touch      id: 10    type: TOUCH     
Wacom Intuos PT S Pad pad           id: 11    type: PAD       
Wacom Intuos PT S Pen eraser        id: 18    type: ERASER 

Is there one last minor glitch remaining somewhere in CTH-480 support in 14.04?

---

### Post by mörgæs on 2015-12-25
> **anton-tagunov said:**
> 
Is there one last minor glitch remaining somewhere in CTH-480 support in 14.04?

Likely. 
You could try a live boot of 15.10 for comparison.

---

