---
title: "Ubuntu won't even boot up???"
date: 2008-10-17
forum: General Help
---

### Post by xwat17x on 2008-10-17
okay, so i installed beryl last night and was messing with it,

I changed one of the settings and the screen went black, but i still had a mouse.

So i didn't know what to do.

I pressed alt+ctrl+f2 i think and this log in (cmd style) thing popped up, it said login info was wrong. i couldn't get back to anything, so i turned my computer off.
Now when i go back to ubuntu, the boot screen comes up and loads but then its just a black screen.

Anyone know what to do?

---

### Post by xwat17x on 2008-10-17
Anyone?

---

### Post by xwat17x on 2008-10-17
?

---

### Post by snova on 2008-10-17
It sounds like a video configuration issue.

The Ctrl-Alt-F2 is a virtual terminal. I don't know why it would give an error message when you tried to login, but if you had succeeded, you would have been treated to a command line prompt.

The next time you try to boot it, press Ctrl-Alt-F1 (just another virtual terminal, like F2, F3, F4, ... up to F7, where the X session is), log in (unless you can't, then I don't know what to do), and try removing the beryl packages.

If that doesn't help, it's probably X misconfiguration. Get back into the terminal and back up /etc/X11/xorg.conf, then try running "dexconf" (as root, with sudo), the job of which is to automatically configure the X server. It should at least get graphics working again, though potentially at a bad resolution.

And if you're still stuck, somebody more knowledgable will have to help.

---

### Post by jhernandez1270 on 2008-10-17
you could try rebooting and at the Grub stage hit the ESC key...then select the recover mode

---

