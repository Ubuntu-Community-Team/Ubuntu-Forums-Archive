---
title: "brightness osd on thinkpad x40"
date: 2008-09-17
forum: Hardware
---

### Post by tqt1586 on 2008-09-17
I had a problem with the brightness On Screen Display not showing up when I pressed 'FN+PGup' or 'FN+PGDN'.  After looking for hours and trying everything from kernel hack to scripts; I found a much easier solution.

Go into the bios with 'F1' key at the IBM logo and under 'Display' change it to 'Internal PCI' for video and 'Laptop LCD' only for screen.  Reboot and it will work.  This will generate a 'brightness' file that previously was not in /proc/acpi/ibm.  After that you can go back to the bios and change it back to what ever you had before yet the OSD will stay.

Another way without doing the bios thing is to plug in an external monitor once.

I'm not 100 percent sure it will work for everyone so I'd like some feedback, but for me it worked great.

Cheers!

---

