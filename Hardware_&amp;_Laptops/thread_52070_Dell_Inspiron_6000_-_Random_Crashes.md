---
title: "Dell Inspiron 6000 - Random Crashes"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by Strife on 2005-07-26
So every once in a while, when I have a slightly high load, my Inspiron 6000 just hangs -- I have no control of the mouse or the keyboard, and any music being played stops playing. When I say slightly high load, I mean generally I'm running Rhythmbox, Acrobat, Firefox, and Synaptic (I'm pretty sure most of the times this has occurred, Synaptic has been in the installing stage, i.e., post download of a package).

My two-pronged question is then this: What kind of logs can I check to try to see what the problem is, and does anyone else have a similar problem/know what to do about it?

---

### Post by s_p_a_r_k_y on 2005-07-26
check the /var/log/system and /var/log/messages ...but usually if the kernel hangs it wont spit out anything to those files...sadly...If you can get it to crash while you in the console, you might be able to see what caused the kernel panic?

Does this happen when you are connected to power or on battery? My laptop only crashes when not hooked up to battery...whihc I'm not sure of either.

Also...have you tried maybe using vesa drivers instead of other video drivers like nvidia or fglrx?

Try turning off powernow or anything which causes the CPU frequency to change.

---

### Post by Strife on 2005-07-27
It happens when I'm plugged in.

I suppose I could turn off the power management stuff, seeing as I never got suspend to work properly anyway, but I kinda want to eventually get around to making it work...

Oh well. At least this isn't too frequent a problem. I just hope it doesn't get worse.

---

### Post by hod139 on 2005-07-27
I also have the same laptop and the same problem, random lockups.  I've also wondered if it is the video drivers, I have an ATI MOBILITY RADEON x300 PCI Express x16 graphics card, and maybe pci express graphics support isn't 100% stable yet for notebooks? Or maybe it is the fglrx driver? I am using the fglrx drivers because I need 3D support.

If anyone has any suggestions, they would be appreciated.

---

### Post by zho40 on 2005-07-28
I have the 6000 as well, try keeping a non blank cd in the cdrom drive.  That fixed it for me no crashes in over two weeks.  If that works you can patch your kernel check out [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)

---

### Post by hod139 on 2005-07-28
[QUOTE=zho40]I have the 6000 as well, try keeping a non blank cd in the cdrom drive.  That fixed it for me no crashes in over two weeks.  If that works you can patch your kernel check out [http://rtr.ca/dell_i9300/](http://rtr.ca/dell_i9300/)[/QUOTE]
 That has got to be the strangest fix I have ever heard of.  I will try it out and see what happens.  Thanks for the reference too.

---

### Post by jc3835 on 2005-07-29
I've had this happen to me a few times recently.
It seems to always happen when I'm loading a new page in Firefox... but then it could be that I am ALWAYS loading a new page in Firefox.  :) 
I'm still using the default drivers... never installed ATI drivers, at least not yet.

---

### Post by c0rderr0y on 2005-07-29
i dont seem to have this problem... i have the ATI m300 also

---

