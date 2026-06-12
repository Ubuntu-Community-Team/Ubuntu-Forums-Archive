---
title: "powersave vs powernow vs cpufreq"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by arashb on 2006-11-29
Can anyone tell me the difference between powersave, powernow and cpufreq?
I am using edgy on a t42, and I want to get the most out of my battery life (as my laptop dies after 1.5 hours, vs 3.5 hours in Windows XP). What could I do to improve battery life? How can I get the HD to spin down? How can I manually set the CPU speed (or have it go to the lowest setting of 600 MHZ when running on battery)? Is there a GUI tool to make this easier that would be integrated in say the gnome cpu frequency applet?

Also, does anyone know how to activate the IBM Shock Protection for the hard drive under Ubuntu?

Thanks

---

### Post by neoflight on 2006-11-29
> **arashb said:**
> Can anyone tell me the difference between powersave, powernow and cpufreq?
I am using edgy on a t42, and I want to get the most out of my battery life (as my laptop dies after 1.5 hours, vs 3.5 hours in Windows XP). What could I do to improve battery life? How can I get the HD to spin down? How can I manually set the CPU speed (or have it go to the lowest setting of 600 MHZ when running on battery)? Is there a GUI tool to make this easier that would be integrated in say the gnome cpu frequency applet?

Also, does anyone know how to activate the IBM Shock Protection for the hard drive under Ubuntu?

Thanks


ithink 600 is a good value to go with. it will override the settings when necessary. i have the same concern over shock proctection. i dont think it exists now. 

did u manage to get the forward backward buttons working for the browser?

---

### Post by arashb on 2006-11-29
I figured out the shock protection.

first:
 sudo modprobe hdaps

Then install the hdaps-utils package

Once that is installed, run hdaps-gl and you can watch your laptops position. Pretty cool (didn't think they would have carried this over from what they had in Windows)

---

