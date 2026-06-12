---
title: "Wacom Bamboo Problems"
date: 2008-08-25
forum: Hardware
---

### Post by shiznatix on 2008-08-25
Ok I got a Wacom Bamboo Fun A6 Wide (CTE-450) tablet for my laptop. I installed it and got everything working just fine and dandy. The problem is that a few months ago, out of nowhere the thing just stopped working. I used to have to have it plugged in when I booted up for it to be recognized but now it won't come up at all. When it is plugged in the light turns on signifying that it has power but thats about it.

I am not sure why this has suddenly stopped working. Can someone give a bit of advice my way maybe to get this thing back up and running?

---

### Post by shiznatix on 2008-08-28
*bump

does anyone know why this might have just stopped working for no reason?

---

### Post by Berethorn on 2008-09-01
This happened to me too. It seems to be caused by a a new linux kernel: 2.6.22-15. The tablet works if I manually start the computer with kernel 2.6.22-14 from the GRUB menu. I have the same problem (and solution) opening a virtual machine with vmware.

So that seems to be the cause. I don't have the knowledge to find a more permanent solution. Maybe it's as simple as reinstalling updated wacom drivers?

---

