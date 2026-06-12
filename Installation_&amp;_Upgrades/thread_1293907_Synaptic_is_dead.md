---
title: "Synaptic is dead"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by MarkJBrader on 2009-10-17
Last night I installed Timevault, thought it was okay, went to bed.
Today I try to run Synaptic and it brings up a box that says:

E:dpkg was interrupted.  You must manually run 'sudo dpkg --configure -a'
E:_cache->open() failed. Please report.

So I open a terminal, and try the 'sudo dpkg --configure -a' 
I cannot see what happens.  Just a few lines print out, then the screen blanks and goes to the login, except that the mouse and keyboard do not work, so I end up having to power-cycle the PC to get back in.

How do I get out of this trap?

Thanks.

Mark

---

### Post by MarkJBrader on 2009-10-17
All is now well.  I managed to remove TimeVault from the init sequence by hand, reran the sudo dpkg --configure -a succesfully, and then use synaptic to clean the rest of it out of the system.

Mark

---

