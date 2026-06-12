---
title: "Help! System crashing (Virtual Resolution setting)"
date: 2009-10-21
forum: Hardware
---

### Post by LiamG on 2009-10-21
I'm using Jaunty on an HP Mini 1000. I was using a projector today and when I changed the display settings accordingly it asked me to create a "virtual resolution" (I don't know what this is) and told me that I had to log out and in again. I did this and the projector worked find. However, ever since I unplugged the projector, the whole system has been very unstable. It appears to me that my video drivers have been corrupted. Here are some of the symptoms:

-The Gnome visual effects were turned off and I can't turn them back on. (When I try, it says "searcing for system drivers" and then can't find them)
-The screensaver runs very slowly.
-The screen shudders every minute or so.
-Once or twice, the screen has gone entirely blank and I have to cut the power.
-If I hibernate, the system boots up to a blank screen.

Obviously, this renders my computer close to unusable. I have no idea where to start looking for a fix, other than to reinstall the whole OS, which would be a great hassle. I'm pretty sure that it's not a hardware problem, as Ubuntu runs fine on my USB drive. 

Can anyone out there help?

---

### Post by Dark_Stang on 2009-10-22
Open up a command prompt and run "glxgears". Do the gears run smoothly or do they run smooth for a couple seconds then run really choppy?

---

### Post by LiamG on 2009-10-22
The gears run very smoothly. My screensaver, however, (Hypertorus) does not.

I've found that the system is stable in recovery mode, although the graphics are still stunted. If the worst comes to the worst, I can run it like this until 9.10 comes out next week and then do a clean install. Still, it would make me very happy if someone could help me identify and fix the problem in the mean time.

---

### Post by Dark_Stang on 2009-10-22
If the gears run smoothly then hardware acceleration should be working fine. If you go back to System > Preferences > Display are you able to disable the fake 2nd display and set your main monitor back to normal?

---

### Post by LiamG on 2009-10-22
The Display settings are just the same as they always are. The second monitory doesn't appear since I unplugged it.

---

### Post by LiamG on 2009-10-22
Perhaps I can refine my question. How do I use the recovery console to identify and solve the problem? I am assuming that the recovery console is similar to Windows safe mode, but I don't really know how to use it, since I'm still relatively new to Ubuntu.

---

### Post by LiamG on 2009-10-23
Problem solved! The "fix graphics problem" option in the recovery console seems to have done it. I'd still be interested if anyone can tell me what happened and how to prevent it in the future.

---

