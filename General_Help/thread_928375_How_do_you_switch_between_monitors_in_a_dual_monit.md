---
title: "How do you switch between monitors in a dual monitor setup?"
date: 2008-09-23
forum: General Help
---

### Post by skralljt on 2008-09-23
Hello all, I recently acquired a second monitor and plugged it in to the spare slot on my motherboard.  I want to play games on my porch so I put it out there and first I was trying to use it with twinview, and it worked but since it is on the porch and I can't see it it was problematic because I would lose part of the taskbar visually, and fullscreen would send over half the program to the other, out of sight, monitor.  Next I tried the multiple x-session with nvidia-settings, and it appears to be what I want: two separate instances of xfdesktop.  Unfortunately, I cannot access the other desktop!  I can't get the mouse over there, I can't send programs to it.  I think it is the same xfdesktop because when I bring my computer out of screensaver, both monitors will come out of screensaver but the password dialog is not visible on the second monitor on the porch, only my first monitor.
Is there some commandline to switch which monitor is getting which session?  I had a party a few nights ago and I think someone who was screwing around with the music playlist accidentally accessed the other desktop because there is a pdf open on it but I don't know how they did it, and there is no pdf open in htop that I can see.
Can anyone tell me how to switch?  There are two xfdesktop sessions in htop but they both point to display 0:0.  I'm using the binary nvidia drivers.

---

### Post by lian1238 on 2008-09-24
I haven't spent a lot of time with a dual monitor setup. But from what I remember, when you go off the edge to the right on the first screen, the cursor should come up out from the left edge of your second. So, in a sense, they're connected side by side.

When you did TwinView, you get one long screen, so the taskbar items that used to stick to the right were teleported to the second screen. But if you choose "clone" in TwinView, well.. you'd get a clone.

IMO, you should use clone instead of separate X screen. I mean, how are you gonna use the 2nd X when you can't see it?? :lolflag:

---

