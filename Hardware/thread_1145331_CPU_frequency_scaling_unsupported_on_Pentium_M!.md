---
title: "CPU frequency scaling unsupported on Pentium M!"
date: 2009-05-01
forum: Hardware
---

### Post by endre on 2009-05-01
Hi guys, I see this has been discussed multiple times in the past, but not with Jaunty. Essentially, the problem is that ever since a release almost two years ago now (I believe it was 7.10) my 1.6 GHz Pentium M (1 Gb RAM) has become increasingly sluggish when running Ubuntu. In fact, I am currently unable to run it smoothly even at medium graphics settings. So I must admit, I have for long periods abandoned Ubuntu and relied on Windows (*shudders*) for most of my work.

However, I have now returned again to give it another chance with Jaunty, and I think I have stumbled across the basic problem. According to the "CPU Frequency Monitor" applet (yes, I am no tech-wiz, it really took me this long to figure it out) frequency scaling is "unsupported" on my system. It claims that when running at 597 MHz, it is actually running at 100%! (and no, it does not change at all when running graphics intensive apps such as VLC)

Again, being no tech-wiz, I am not hoping to be able to regulate this manually, but I was hoping to find a way to make Ubuntu manage my CPU speed more efficiently. Is there any way to do that?

Cheers!

---

### Post by davidjparfitt on 2009-05-01
try going to the site below;
 
[http://gentoo-wiki.com/](http://gentoo-wiki.com/)
 
There are patches that allow CPU voltage control. Only problem is that this will affect the battery life, it will reduce dramatically depending on what kernal you use.
 
Hope this helps!!!

---

