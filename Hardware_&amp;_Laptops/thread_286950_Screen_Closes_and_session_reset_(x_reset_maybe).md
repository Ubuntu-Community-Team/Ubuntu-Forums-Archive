---
title: "Screen Closes and session reset (x reset maybe?)"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by likwidoxigen on 2006-10-28
I'm running edgy on a Dell C810 and every time I close the screen I get logged out, it looks like an X reset, however I can't be sure and I don't get any errors. 

This is NOT a suspend or hibernate issue. I have the screen set to do nothing on close and this still happens. My original setting was to blank screen, and the same problem still occcured.

Ubuntu has been on here since Breezy with no problems with closing the screen till now. 

I've searched all through the forums and gotten nothing. Any ideas?

---

### Post by likwidoxigen on 2006-10-28
I put in a bug report for it because the logs appear to say that it can't re-initialize the server. Seems like an X server problem and now that it's a new build with AIGLX that could be the issue. I've tried running with no accel however that hasn't worked. I tried the generic ATI driver and failed with that one also.



Oct 28 10:51:38 localhost kernel: [17238325.204000] video bus notify
Oct 28 10:51:39 localhost gnome-power-manager: (bryce) Doing nothing because the lid has been closed on ac power
Oct 28 10:51:40 localhost kernel: [17238327.392000] video bus notify
Oct 28 10:51:41 localhost gdm[16675]: Error reinitilizing server

---

