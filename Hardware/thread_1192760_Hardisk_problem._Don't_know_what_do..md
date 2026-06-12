---
title: "Hardisk problem. Don't know what do."
date: 2009-06-20
forum: Hardware
---

### Post by ofir_k on 2009-06-20
Hello,

After two brutal shutdowns, the HD started to make problems.

The main problem seems to be a bad sector in the HD.

I don't really know if this is the problem, and how to deal with it.

I will really appreciate any help!

---

### Post by khelben1979 on 2009-06-20
If it's about bad sectors which causes problems, you always have [SpinRite]("http://en.wikipedia.org/wiki/Spinrite") (Windows software I know, but maybe you're running dual boot or have access to a Windows system?)

If it's about something else, for example that the filesystem has been damaged. Then you need to repair it with a tool such as [fsck]("http://en.wikipedia.org/wiki/Fsck").

---

### Post by ofir_k on 2009-06-20
I have Windows XP in dual boot. Does SpinRite will be able to repair the ext3 partition? Does PC-Doctor knows how to do it?

What is a bad sector exactly? A format to that partition will solve the problem?

---

### Post by khelben1979 on 2009-06-20
Check out the SpinRite videos on [this page]("http://www.grc.com/sr/themovie.htm"). It will explain how it works.

SpinRite finds [bad sector]("http://en.wikipedia.org/wiki/Bad_sector")s and makes them unusable for the harddrive to access them and thereby solving the problem.

---

