---
title: "Reset screen resolution"
date: 2008-10-27
forum: General Help
---

### Post by hrMeyer on 2008-10-27
Hi!

I have for a long time been trying to edit the screen resolution, but when I did, I ended up messing up ****. Now the screen is blurry and hard to look on. Is there a way to reset the preferences as they were before? Thanks in advance.

And one little bonus question: My screensaver is not working. When one minute is elapsed, then the screen goes black for one tenth of a second, and then everything is back to normal - but no screen saver!

(Almost) all answers appreciated.

Thanks.

---

### Post by cdtech on 2008-10-27
Just boot into "recovery mode" and type:
sudo dpkg-reconfigure xserver-xorg

This will reset your xserver.

---

