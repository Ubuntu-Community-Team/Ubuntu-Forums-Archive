---
title: "Display fails on suspend, logout, switching to terminal"
date: 2009-10-30
forum: Hardware
---

### Post by NertSkull on 2009-10-30
So I had this problem in Jaunty, and I upgraded to Karmic today hoping it would fix it, but still have the same issue.

If I log out, or switch users, or go to suspend mode and log back in, my display fails to load correctly.  I can see things, but its SUPER shaky and grainy and looks horrible.  

I can post a picture if needed, but its not usable.  If I go into hibernate mode, and then start and login nothing is wrong.  Only if I do ctrl+alt+F1 for terminal, or logout, or switch users etc does it do it.  A fresh boot, either from hibernate or completely off gives me no trouble.  I would really like to be able to suspend my computer, or let my wife switch to her account without needing to first hibernate mine.

Any help would be so appreciated.  I think it has to be something like rebooting the X server, or refreshing it or something.

I'm running an Asus laptop.  I have the NVIDIA GT240M which has given me some problems on its own (even with the new drivers released a few days ago).  So that may have something to do with it.  I have to tell the x server to ignore the size check or I get six screens.  But thats a different problem, just putting it out there in case it helps fix this one.  Thanks everyone, I really appreciate the help.

---

### Post by NertSkull on 2009-11-01
So I tried going to a terminal to stop gdm and then restart it but it doesn't help the problem.

It must be something more than that because even when I go to the terminal (through ctrl+alt_F1) the screen is fuzzy and not out of synce.  

Is there a command I can use to restart the entire graphical display.  Not just the X-server??

---

### Post by NertSkull on 2009-11-03
Sorry everyone, I hate bumping, but someone has to have an idea of at least something I can attempt, even if it doesn't work.  Cause I'm really stuck.

---

