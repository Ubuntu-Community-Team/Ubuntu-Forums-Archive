---
title: "[SOLVED] Permanent Floppy Disk Drive Light"
date: 2008-10-19
forum: General Help
---

### Post by scouser73 on 2008-10-19
Since installing Intrepid Ibex, I have had no problems whatsoever, there is just one thing puzzling me though. The light on the floppy disk drive stays on permanently, the drive itself has never been used. It's not a problem as I'm not going to use the floppy drive, but can anyone think what has caused the light to be on continually?

---

### Post by TheLions on 2008-10-19
> **scouser73 said:**
> Since installing Intrepid Ibex, I have had no problems whatsoever, there is just one thing puzzling me though. The light on the floppy disk drive stays on permanently, the drive itself has never been used. It's not a problem as I'm not going to use the floppy drive, but can anyone think what has caused the light to be on continually?

powercable isn't connected properly!

reverse it by 180°

---

### Post by scouser73 on 2008-10-19
No, it's not that, as the light wasn't permanently on when I had Hardy Heron installed it's only happened sice I installed Ibex.

---

### Post by Gullee on 2008-11-12
My floppy light is also on all the time in U_I-8.10. Anyone know how to fix this? Thanks!

---

### Post by TheLions on 2008-11-13
not a helpful solution: disable it in BIOS

---

### Post by plucky on 2008-11-13
> **Gullee said:**
> My floppy light is also on all the time in U_I-8.10. Anyone know how to fix this? Thanks!

Try from a terminal ```
sudo modprobe floppy
``` which will load the floppy driver.If that works,then to make sure the driver loads on every reboot ```
gksudo gedit /etc/modules
``` and add the word **floppy** on a newline.


Good Luck

---

### Post by user11 on 2008-12-07
Thanks Plucky, works great!

---

