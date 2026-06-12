---
title: "LCD monitor being detected as CRT 9.10"
date: 2009-12-30
forum: Hardware
---

### Post by D@wson on 2009-12-30
Hello all I hope you can help me setting up my graphics card which is a 9800GT and my monitor an Optiquest Q2202wb and Ubuntu 9.10.

My monitor has a native resolution of 1680 x 1050 (16:10) I have installed the recommended nvidia drivers for my card and i cant get the resolution above 800 x 600 i also noticed its detecting my monitor as a crt. I have the monitor plugged into a VGA to DVI adapter and was wondering if this could be part of the problem. 

The defualt display manager in Ubuntu cant detect my monitor either and lists it as unknown and will only let me use 800 x 600 also.

  Thanks,
  Richie

---

### Post by D@wson on 2010-01-03
Bump?

---

### Post by mikeh on 2010-04-28
If the monitor auto-detect does not work, you can always do it the old-fashioned way and edit /etc/X11/xorg.conf

Just add some lines in the "Monitor" section. e.g.

    HorizSync       31.0 - 83.0
    VertRefresh     50.0 - 76.0

Or whatever your monitor supports.

Then restart X, and the GUI should offer suitable settings.

---

