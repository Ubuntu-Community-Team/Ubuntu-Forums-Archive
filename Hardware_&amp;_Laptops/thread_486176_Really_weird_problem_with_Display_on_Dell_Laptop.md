---
title: "Really weird problem with Display on Dell Laptop"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by mav5150 on 2007-06-27
Hey everyone, 

I just finished installing Ubuntu on a laptop that I found sitting in a box in my garage. From what I could gather from it the laptop is a Dell C610 with 1.2Ghz Pent III, 256MB of Mem, and a 20 GB HD. The computer use to have Windows 2000 on it, but I wanted a strictly Linux laptop so I had Ubuntu install over that partition to get rid of windows. When Ubuntu loaded up the screen was split in half with a strange void in the middle of the screen and the right side of the desktop is duplicated twice on the screen, once before the void and once after the void. I assumed it was a display setting error that I needed to fix either in the terminal or using system preferences, but the problem is that the void is right where the tap for system settings is at, so I can't read or find the system settings button to make the changes. If I open up a terminal window I can shift it all the way to the left side of the screen so I can read it and type into it but I can't seem to find where to make the changes (I've tried looking for the X11 folder using sudo gedit /etc/X11/xorg.conf but nothing came up and the message that did appear gets cut off by the void). I don't know where else to look except to ask for help here and see if anyone knows how I can pull up the screen settings without having to go to System->Preferences->Screen Resolution since the void cuts out the whole menu after preferences. I even tried to just hit the s key while the preferences tab was open to see if it would jump down to Screen Resolution but every time it was a different option that popped up (like Screen Saver and some other ones). Thanks for any help and I hope this made some sense, I just never seen a problem like this before so it was hard to explain.

---

### Post by mav5150 on 2007-06-28
Nevermind, I was actually able to fix the problem. I used the nano text editor and shrunk the window down as much as possible and found that the Monitor section was missing the VertRefresh and HorizSync sections. I couldn't see it earlier since the window was still too big and the void in the middle blocked it. All fixed now :D

---

