---
title: "how to use external screen as main screen, and closing the laptop?"
date: 2011-05-17
forum: Hardware
---

### Post by amityak on 2011-05-17
Hi All

In 11.04: How do I turn off the Laptop screen and use just the external screen? So that i can close the laptop without my external screen going off?

Please note i want to see all the menus as well (using Ubuntu Classic view)

Thanks for answering (:

Amit

---

### Post by teachop on 2011-05-17
> **amityak said:**
> Hi All

In 11.04: How do I turn off the Laptop screen and use just the external screen? So that i can close the laptop without my external screen going off?

Please note i want to see all the menus as well (using Ubuntu Classic view)

Thanks for answering (:

Amit
Try running gconf-editor.  Go to the apps|gnome-power-manager|buttons.  Set the value of lid_ac to "nothing".

---

### Post by amityak on 2011-05-17
hi teachop, thanks for the reply.

Do I have to restart in order for changes to take effect? I tried logging out and in again and it still shuts both screen if i close the lid :/   

and what about the desktop panels? how do I move those into the external screen?

---

### Post by teachop on 2011-05-17
> **amityak said:**
> hi teachop, thanks for the reply.

Do I have to restart in order for changes to take effect? I tried logging out and in again and it still shuts both screen if i close the lid :/   

and what about the desktop panels? how do I move those into the external screen?
Sorry that didn't work right off.  I don't remember at this point if I had to reboot or not, but it does work on this machine.

I had to use the Monitors setting program to put the external monitor on the left.  I could not disable the laptop screen, that made the whole thing go crazy and start to flash, and it was hard to get back from that.

I don't think multiple monitor support is very good yet in this version.  I have an Intel i3 laptop with integrated intel graphics, and had to fight with it.  At work I have a Intel i7 with nVidia, had to fight with that too, and actually have to change settings between running as a laptop and as a "desktop".  Not smooth at all yet.

---

### Post by amityak on 2011-05-17
yeah same here... flickering and going mad when i try to turn off the laptop's screen. had to move to console view (alt+ctrl+number), plug-out and then back to X view (alt+ctrl+7) to make everything stable again.

well, maybe someone else has an idea how to get this done... this is an i5 machine with a Radeon graphics-chip.

---

### Post by teachop on 2011-05-17
What problems do you still have, can you close the lid now?  You can switch primary monitor with xrandr, if you cannot get the panels to flip with Monitors, but then we need to figure out how to make that stick through reboot.  Why oh why don't they have these options where you can USE them instead of "xrandr" and "gconf-editor" being so user unfriendly.

It is amazing to me that you have ATI monitor problems, I have nVidia and Intel problems.  Which ones work.

If you fool with it eventually it will sort out, I can attest to that.

---

### Post by amityak on 2011-05-17
this helped to switch monitors:

[http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions](http://www.thetechrepo.com/main-articles/502-how-to-change-the-primary-monitor-in-ubuntu-or-other-linux-distributions)


very.... veryy ugly !!

---

### Post by teachop on 2011-05-17
> **amityak said:**
> very.... veryy ugly !!
Really!

Good job getting it sorted out, others will find the thread when they need it.  Too many settings have been removed from the video GUI utility for no good reason.  Same for goes for trackpad settings....

---

### Post by amityak on 2011-05-17
do you know how to report this post as solved?

---

### Post by teachop on 2011-05-17
> **amityak said:**
> do you know how to report this post as solved?
Hit the drop down list called "Thread Tools" at the top of the page, it is the last entry in the list.

---

