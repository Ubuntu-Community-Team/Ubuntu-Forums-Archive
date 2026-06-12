---
title: "Dell D820 First Install Issues"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by clsvarog on 2007-01-10
After reading a few howtos and reviews of Ubuntu on a D820 i decided to make the switch (was previously using debian).  Unfortunately i've ran into a few problems that haven't been mentioned in the how-tos and haven't been able to find any info to resolve them by googling.

Issue 1:  Focus is crazy.
  When i have multiple windows open (mostly multiple terminals).  I find the response when trying to change focus to be awkward at best.  Sometimes it will switch fine with the mouse, sometimes alt-tabbing is the only way to switch focus, occasionally neither works and i have to alt-tab / alt-ctrl-esc around a bit until something grabs focus and i can then either mouse or alt-tab to what i want.  I have no leads as to what's causing this and don't know if i'm explaining what's happening well enough, but it feels like the pointer gets disassociated from the window manager (or something).

Issue 2: Typing is crazier.
  I've seen reports of this on google and posted this issue in another forum, but haven't encountered a solution that works for me (yet).   While typing occasionally one keypress will be read as 2-5.  This is definitely a recent issue as it didn't occur in debian, the ubuntu live cd or a knoppix cd.

If anyone has solutions or experiences with either of these problems, please let me know.

Thank you.

---

### Post by tcrroadie on 2007-01-10
Just a quick thought.  Since you mentioned that the two issues you are having did not occur when running Ubuntu from a live cd, you may want to try comparing the xorg.conf file that was created from running from live cd and the one the installer created on your system.  

Possible error in xorg.conf

---

### Post by Delvien on 2007-01-10
My D820 has experienced none of your problems, and i installed from the non-live install iso burned to a disk

---

### Post by clsvarog on 2007-01-11
I found a 'solution' last night in turning acpi off at boot.

Solution is in quotes because while this solves the significant issue of stuttering keystroke and losing window focus/ wonky mouse behaviour it does so at the cost of acpi functionality.

I'll likely play with different setting to see if there are any specifics that are causing the crash and report back here if i have any other news.

---

### Post by nexus_2006 on 2007-01-11
I have been running Dapper on my D820 for over a month now and have experienced no such troubles.  Wifi was a bit frustrating though.  Anyway, I have noticed on this laptop that wonky mouse behavior is just part of the experience.  Sometimes the mouse button will not work for no apparent reason and other times it desiced it wants to 'hide' the pointer in a corner of the screen.  This also happened to me under windows though.  Hope you get it straightened out, I have had nothing but good times with my install.

---

