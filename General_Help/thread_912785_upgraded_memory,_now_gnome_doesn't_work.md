---
title: "upgraded memory, now gnome doesn't work"
date: 2008-09-07
forum: General Help
---

### Post by bake578 on 2008-09-07
I have an old Thinkpad A30 with an ATI M6 video card. I was running Ubuntu fine with 2 256MB sticks of memory, but when I upgraded to 2 512MB sticks Ubuntu doesn't work properly.

I can log into to Failsafe Terminal session, but if I try gnome I get my background, but nothing else is visible. I can sometimes bring up a terminal window with my keyboard shortcut; however, it will close after a few seconds and then Ubuntu reboots. Everything works from the terminal, just no gui.

I ran the memtest and everything passed and the BIOS recognizes that I have 1GB RAM installed. Do I need to reconfigure something in Ubuntu after upgrading the memory?

Please help!

---

### Post by ladr0n on 2008-09-07
You shouldn't have to reconfigure anything when adding new RAM.

The command 'free' will give you stats about your RAM.  'Total' should be a little over 1000000 for 1 GB.  If you don't see anything odd there, try looking at dmesg (command 'dmesg -tail' will give you the end of it) right after starting gnome.

If you still find nothing, as unlikely as it sounds, this might not even be related to the new RAM (especially is memtest doesn't find anything wrong with it).  If you still have them on hand, you might try putting the old RAM back in to see if that fixes the problem.  Post back if you find anything.

--edit--

I've actually had Xorg do something similar to that recently (it affected gnome and wmii, too), though rebooting fixed it.  Has there been an Xorg update recently perhaps?

---

### Post by bake578 on 2008-09-07
I didn't think that anything should need to be reconfigured, but SOMETHING isn't working properly. I put the other memory back in, and the same thing happens. Running the 'free' command showed the correct amount of RAM. dmesg didn't display any errors as far as I could see. If I can open a terminal I can get nautilus and firefox open by manually starting it... so maybe something happened with the session manager by coincidence? I'm at a loss. Any other ideas?

---

### Post by bake578 on 2008-09-07
After a painful day of playing with things, I finally realized that for some reason gnome-panel wasn't loading at startup. I started it, and now everything seems to be working again. Weird, but an easy fix once diagnosed. (At least that's what I THINK the problem was...)

---

