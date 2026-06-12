---
title: "how to show boot output"
date: 2008-12-01
forum: General Help
---

### Post by rotlas on 2008-12-01
Hello, does anyone know how to enable boot info and shutdown info printing for ubuntu during booting. Currently when I do these operations, the only thing I see is either black, a cursor or the progress bar.

---

### Post by __Ryan__ on 2008-12-01
Go into /boot/grub/menu.lst and locate the "kernel" line.

Go to the end of the line and place a "#" before the "splash" keyword.

Save the file and reboot, there will be no more splash screen.

---

