---
title: "[SOLVED] Suspend problem: laptop resumes ok, but X11 is blank"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by brandon30x on 2007-10-24
After a fresh install of Gutsy, my Compaq V2000 (V2010US) successfully suspends to ram and resumes. However after logging back in (through xscreensaver?) the x session is blank showing only my mouse cursor. I can tell my application windows are still there because I can see the cursor change as i go over text areas etc..  I can also change terminals to the text login and everything works, but changing back to VT7 I still have an all black screen with only a cursor. If I kill xorg (ctrl-alt-backspace) x restarts fine, but then whats the point of suspending! :(

Many people have suspend problems with Gutsy, but after some searching I didn't find anyone with my same problem. And its not an ATI or NVIDIA problem because this is a centrino laptop using intel integrated graphics and the "intel" xorg driver. Because suspend actually works, I am hopeful that there is an easy solution to my problem. So I am asking if anyone else has this problem or knows and answer to please respond in this thread.
Thanks,
-Brandon :confused:

---

### Post by #Reistlehr- on 2007-10-24
edit the file:

gksudo gedit /etc/default/acpi-support 

set these:
POST_VIDEO=false
ENABLE_LAPTOP_MODE=true

---

### Post by brandon30x on 2007-10-24
Reistlehr, first of all thank you for your quick reply. I did as you suggested and then rebooted. Unfortunately it had no effect, I have the same problem.

I tried a couple of other things though. I tried turning off desktop effects (they were set at the mid-value by default) and the problem went away. I tried suspending several times, and after rebooting. I can definitely say that it is compiz that is causing my problem. Also after turning the effects off, then turning them on through the gnome appearance settings the screen immediately goes black.

So the solution is to disable compiz/desktop effects, although this is more of a work around than a solution,
Thanks,
-Brandon

---

### Post by jenast on 2007-10-25
In the compiz settings manager->general, disable "sync to vblank".
Seems to work together with the fix above for my dell D820. Not sure on the consistency yet...only tried it just now.

/jenast

---

### Post by brandon30x on 2007-10-25
I tried every combination of "sync to vblank"=on/off and POST_VIDEO=true/false and my x session still resumes blank (when compiz is on of course). Thanks for the information,
-Brandon

---

### Post by spotspot on 2007-10-30
hm i have an ibm x40 that worked fine with 7.4 and with 7.10 had this problem.  further, the external monitor toggle key Fn-F7 did nothing.  i tried disabling the gloss without effect.  so based on a search i switched to the vesa driver and that's fine now -- but then GLUT/DRI is really slow.

---

### Post by spotspot on 2007-10-31
> **spotspot said:**
> hm i have an ibm x40 that worked fine with 7.4 and with 7.10 had this problem.  further, the external monitor toggle key Fn-F7 did nothing.  i tried disabling the gloss without effect.  so based on a search i switched to the vesa driver and that's fine now -- but then GLUT/DRI is really slow.

i should add: editing the acpi settings as described above by Reistlehr fixed it.

---

