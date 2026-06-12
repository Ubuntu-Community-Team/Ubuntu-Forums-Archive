---
title: "Re-scan hardware"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by mechanic on 2005-11-02
Does anyone know the procedure for rescanning hardware to make any changes to the installation if one changes the hardware (updates the graphics, whatever)? I don't see this described in the how-to anywhere.

m.

---

### Post by mechanic on 2005-11-07
Just to update the picture, I changed video cards and the monitor today, the machine wouldn't boot the x-server but from the console I could run:
"sudo dpkg-reconfigure -phigh xserver-xorg" and this did its thing. Reboot and all came up at the new higher resolution, very nice. I particularly like the way the -phigh switch tells the system not to ask any awkward questions and just work it out for itself!

m.

---

### Post by Teroedni on 2005-11-07
So everything works well?

---

