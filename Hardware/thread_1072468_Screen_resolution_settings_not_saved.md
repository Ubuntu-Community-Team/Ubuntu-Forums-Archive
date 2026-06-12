---
title: "Screen resolution settings not saved"
date: 2009-02-17
forum: Hardware
---

### Post by superdx on 2009-02-17
I have a dual monitor setup on a laptop but every time I login the settings all reset to default. I have to go back into the Screen Resolution settings to change them back every time, which can get tedious.

Is there some kind of setting which I am missing? Whenever I finish setting it up in Screen Resolution, it asks me if I want to keep my settings and I always confirm to do so. But it seems like the function is broken

---

### Post by linfidel on 2009-02-17
> **superdx said:**
> I have a dual monitor setup on a laptop but every time I login the settings all reset to default. I have to go back into the Screen Resolution settings to change them back every time, which can get tedious.

Is there some kind of setting which I am missing? Whenever I finish setting it up in Screen Resolution, it asks me if I want to keep my settings and I always confirm to do so. But it seems like the function is broken
I don't know anything about the particular problem, but maybe I can help zero in on the problem.  

One thing that may help - is the 2nd monitor turned on when you first boot the system?  For my desktop, if my monitor is turned off when the display driver first gets loaded (before the grub menu), then the video comes up in VGA mode.  Also, believe it or not, the mouse misbehaves slightly, which I don't understand at all.

If the problem happens even with the monitor turned on, then I suggest a couple of tests that might help.  One is to log out and back in after saving the settings; see if that works.  Try restarting X by pressing Ctrl-Alt-Backspace (make sure you close open apps, as it will immediately log you out and restart X-windows).  If those remember the settings, try doing a restart instead of shutdown.  See if that works.

Then, post the results, and maybe the extra information will help someone come up with more suggestions.

---

