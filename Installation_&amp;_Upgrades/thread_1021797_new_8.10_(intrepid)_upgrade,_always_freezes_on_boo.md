---
title: "new 8.10 (intrepid) upgrade, always freezes on boot"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2008-12-25
I just did an upgrade 8.4->8.10, now when I boot, the progress
bar gets about 1/3 of the way across and it just freezes, hangs,
sits forever.  So I poked around on the forums and there was
noise about similar issues (not exactly this one) and people
mentioned hitting CTRL-ALT-DEL and that it goes.  So I did, and
it does.  But does anyone have any ideas of a better fix?  Or
at least of things to try?

BTW, this is a Thinkpad R61e, generally decent machine which
ran 8.4 beautifully.


Thanks!

---

### Post by didac on 2008-12-27
When you boot, press ESC at the GRUB prompt. Select your Linux line, press 'e' to edit, go down to the line with kernel written on it, edit it to delete the word 'splash', enter and boot. 

Now you'll see lines scrolling that will help you to troubleshoot your problem.

---

### Post by bodhidharma on 2008-12-29
Thanks for the suggestion -- you get the same things that way
that you see with CTL-ALT-F1, right?

Anyway, I've got a slightly different problem, no: it actually
doesn't completely freeze (I guess it never did), it just sits
for *a long time*.  In the other screen showing what it is doing,
it seems that it does this really, really long pause about at
"kinit: no resume image, doing normal boot..."

Any ideas of why?  Is there some sort of service starting which
has problems but has a really long timeout?

Thanks!

---

### Post by didac on 2008-12-31
Once you log in, type in a terminal:

[CODE]dmesg[\CODE]

Many lines will scroll by. There is a timer that tells you how much time each process takes. Maybe you'll get an idea there. If not, analyze the different logs in System => Administration => System logs

---

