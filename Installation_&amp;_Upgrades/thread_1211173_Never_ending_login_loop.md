---
title: "Never ending login loop"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by harpert on 2009-07-12
After upgrading from 8.10 to 9.04 I can't escape a login loop.
- Ubuntu boots up to the login screen without a problem
- after I put my user name and my login password into the input mask i actually can login
  - It shows the menu bar on the top
  - then the old items on the desktop also appear 
  - I even can hear the successfull login sound
Suddenly the desktop disappears and I see a console for just a second and I am back where I started!! at the Login Screen.

I tried with my user account as well as with the root account no difference at all.

However I can successfully perform a login on any of the TTY consoles 

My environment is a simple one. VirtualBox on a MacBook with all the standard settings and 8.10 worked fine!!

One more thing. On the sda1 partition there are still 1.3 G avaialble

Please advice!!

---

### Post by NoBugs! on 2009-07-13
I noticed this on an old computer, the problem was the window-system crashed right after loading the desktop, then it goes back to login. The window-system and graphics software is different in 9.04 and on some computers the graphics won't work correctly :(

---

### Post by harpert on 2009-07-13
That might be true with an old computer. 
However my ubuntu runs on a virtual machine with VESA graphic.
An additional information is that the X-Window system is producing the following log:
    ----  gdm_slave_xioerror_handler: Fatal X error - Restarting  ------
but it doesn't say what caused that error

Maybe somebody out there knows the reason???

---

