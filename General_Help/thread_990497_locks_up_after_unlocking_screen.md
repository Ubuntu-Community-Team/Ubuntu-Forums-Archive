---
title: "locks up after unlocking screen"
date: 2008-11-22
forum: General Help
---

### Post by Lary Grant on 2008-11-22
Ever since upgrading to Intrepid, I've been seeing a problem: when the screen saver activates password protected, and I later unlock the screen, I can see the desktop background, but no icons or panels, so I can't do anything except power cycle.  I have all the power saving options disabled.  What can be causing this?

---

### Post by Lary Grant on 2008-11-26
bump

---

### Post by linux_tech on 2008-11-26
What is your system config?
Does it happen that way for you always or just sometimes?
If you have a laptop, what are youe Bios power mgt settings
I have Intrepid on a desktop and it works fine for me

Try a test set for 3 mins w/ these settings=

Check both options- Activate scrn saver when computer is idle.
Lock screen when screen saver is active.

Look under power management next- 
action slider- Put computer to sleep when inactive for=never
Display- Put display to sleep when inactive for=never

---

### Post by Lary Grant on 2008-11-27
It's a desktop and has Intrepid with the latest updates.  The settings are already as you suggested.... I already had all Power Management options turned off.

---

### Post by linux_tech on 2008-11-27
What is the system config? how much RAM? What video card and 
what video drivers are you using? Intrepid drivers or proprietory drivers?
Do you have swap enabled? How much?  Does this happen during any hibernate or suspend, or just when you use the screen saver lock?

---

### Post by spoon103 on 2008-12-11
I have the same issue with Intrepid.  What I have noticed is that Xorg is taking 100% percent of the CPU after I unlock the screen saver.  I'm using a Dell Optiplex 755 with 1GB of RAM, onboard Intel Corporation 82Q35 video, with standard Compiz stuff enabled.  I noticed I didn't have any swap space assigned.  I added some and I'll check back and see if that fixes the problem.

---

### Post by spoon103 on 2008-12-12
Adding swap space didn't help.  I'll try disabling unnecessary services like compiz and see what happens.

---

