---
title: "External monitor corrupted after 10.10 -&gt; 11.04"
date: 2011-05-21
forum: Hardware
---

### Post by b00n on 2011-05-21
HP Mini (I forget the specific model).  External display worked great under 10.10, I switched to 11.04 the other day and the external monitor no longer works right.  Two failure "signatures":

* If I try to switch over to just the external monitor, no laptop monitor, the lower left is displayed properly, but a black band appears i the upper and right-hand parts.  Curiously, the Ubuntu title bar appears correctly across the top.  So I think the monitor is handled right at the lowest level, but some higher-level piece is confused.

* If I try to display the same thing on both laptop and external monitor, I just get corrupted trash (colored streaks, not moving) across both displays.

Dell 1600x1200 running at 60Hz.  The display is stable, just wrong.

I'd try turning down Compiz effects, but with the new 11.04 UI, I can barely get around.

Any ideas what I should try next?

---

### Post by b00n on 2011-05-21
I switched from Unity to Classic/No effects (log out, select user name, select at menu).  The external monitor works again.

---

### Post by svast on 2011-05-22
Thank you very much for the tip, you saved my day!
Running Ubuntu 11.04 x64 , on a Toshiba R830 (only has Intel graphics): same issues, and same solution :-)

---

### Post by psychetician on 2011-05-23
Same problem!  Same solution!

I'm using 11.04 on a Lenovo x201.  This problem happened when I attached a second monitor, or switched into tablet mode with magick-rotation.

Would be nice to understand the root of this problem tho.  I like unity...

---

### Post by greencookie on 2011-05-26
I am facing a [similar]("http://ubuntuforums.org/showthread.php?p=10863373#post10863373") problem.

Sometimes executing ```
unity --replace
``` helps rectify the problem.

---

### Post by svast on 2011-05-31
@greencookie : do you manage to get unity working on external display with your tip?

thank you

---

### Post by svast on 2011-05-31
@greencookie : do you manage to get unity working on external display with your tip?

thank you

---

