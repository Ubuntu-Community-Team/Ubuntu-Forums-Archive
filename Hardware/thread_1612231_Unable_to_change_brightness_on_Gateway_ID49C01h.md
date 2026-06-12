---
title: "Unable to change brightness on Gateway ID49C01h"
date: 2010-11-02
forum: Hardware
---

### Post by QuantumFX on 2010-11-02
I'm currently using 10.10 64-bit but I've had this problem since 10.04. I googled around and found people with similar problems but none of the solutions seem to work. The most promising solution seemed to be adding acpi=vendor as an argument in grub and it didn't work.

The Fn keys are working normally. I get the popup display from Ubuntu showing the supposed change in brightness without anything changing at all. The slide doesn't work in Power Management either.

My laptop uses Optimus (with nVidia GeForce GT 330m) but I'm stuck with integrated graphics (Intel GMA HD with Core i3-350m).

---

### Post by QuantumFX on 2010-11-06
Bump. This problem is getting very annoying, especially during the night. Is it a firmware or a configuration problem?

---

### Post by Quackers on 2010-11-06
It seems it's a fairly common problem. My brightness won't change. In fact it has never been adjustable from 10.04 to 10.10 (these are the only Ubuntu versions I have used).

---

### Post by garvinrick4 on 2010-11-06
Do you mean you right click on panel and choose add to panel choose Brightness applet and it does not change the brightness of your screen?

---

### Post by Quackers on 2010-11-06
Hello again garvinrick4 :-)
That applet doesn't work for me. When I click on it a slider appears which is all the way to the top and as soon as I try to change it, it disappears :-) It does that in Lucid and Maverick.

---

### Post by garvinrick4 on 2010-11-06
click on it and roll your wheel, will disappear on second click, so one click and roll.

---

### Post by Quackers on 2010-11-06
I just tried that (although I didn't know about it :-) ) and the slider does move, but the brightness doesn't change. Not a major problem as it looks ok as it is tbh.

---

### Post by QuantumFX on 2010-11-06
Same for me. The brightness applet's slider does nothing at all (although it does change with my Fn keys). I find the problem to be quite annoying as it burns right through my laptop battery when it's not connected to AC.

---

### Post by Linducker on 2010-11-29
I am having this this problem as well on the ID59C. Any solutions yet?

---

### Post by Gunner2677 on 2011-05-12
> **Linducker said:**
> I am having this this problem as well on the ID59C. Any solutions yet?

Try this.


  sudo gedit /etc/default/grub


  Change the line GRUB_CMDLINE_LINUX="" into GRUB_CMDLINE_LINUX="acpi_osi=Linux"


  sudo update-grub


  Restart your linux

---

### Post by Linducker on 2011-07-23
Thanks for the reply. Found this exact solution elsewhere but I appreciate still it!

---

