---
title: "How to change default page size from Letter to A4"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by dmuir on 2008-01-30
I've been trying to figure out how to change the default page size in apps to A4. Every time I open up a file, it defaults to Letter. It applies to just about every single program. Just to name a few: Evince, Firefox and OpenOffice.

The default page size for the printer is set to A4, but this doesn't seem to affect anything.

I'm sure this is an issue for anyone not living in the US where A4 is the standard page size.

---

### Post by Boelcke on 2008-01-30
There's an answer here:
[http://ubuntuforums.org/showthread.php?t=292449](http://ubuntuforums.org/showthread.php?t=292449)

...in which Jorge says:

> Solved!

a) I edited the file /etc/paper, removed "a4" and wrote "Letter" (without quotes).
b) I removed and reinstall every printer.

I haven't tried it, but it sounds like a solution!

---

### Post by dmuir on 2008-01-31
/etc/paper didn't even exist.
/etc/papersize did though, but that was already set to a4
I created /etc/paper and put in a4, and now it works!

Thanks!

---

