---
title: "Cannot Start GDM??"
date: 2008-10-09
forum: General Help
---

### Post by anim on 2008-10-09
Ok this one is a bit confusing, here goes.

Today I removed OO-2.4 with synaptic and installed 3.0 (Nice, btw).

Besides that and maybe about two updates through update manager (didn't even pay attention to which ones are there), I did nothing else that affects system internals. Firefox, and OO-3.0 writer only. Finished work, turned off computer.

Now, I just turned on the computer, logged in (I got the login screen) but the desktop never appeared. Even after a 20 minute wait. Restarts and recovery console no dice as well. Console works fine, but since I didn't make in drastic alterations to my system configurations I don't even know where to start in order to fix this thing. Any help will be appreciated. Currently I'm running off a fiesty live-cd on the computer in question so I apologize for the delay in replying to possible solutions, booting into the live cd takes some time.

Thanks again.

8.04 / Current Kernel / ATI restricted driver /

---

### Post by fsmithred on 2008-10-10
You don't like lynx? It's way faster than firefox.

If you're getting a graphical login screen, then gdm is running. If you're logging into a console, try running 'startx' to see if you get to a desktop, and/or try 'sudo /etc/init.d/gdm restart' to see if you can get to a graphical login.

Look in /var/log/dpkg.log and you might see if something you need was uninstalled.

---

### Post by anim on 2008-10-10
I've already tried gdm restart and startx. My x-server is fine, so (seems) gdm up to the point that I login, but my desktop fails to appear.

---

### Post by anim on 2008-10-12
Yeah, so I couldn't figure it out, so i just went recovery mode to root terminal and chmodded my /home/ to 777, then backed it up to an external drive using a live cd. Decided it was as good a time as ever to try 8.10 so I let that rip. Decided to post this for posterity if anyone else has the same problem. Not really a fix, but hell at least you don't loose your files.

Pat

---

