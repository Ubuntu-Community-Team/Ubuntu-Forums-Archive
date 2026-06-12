---
title: "links in thunderbird do not open correctly - any ideas? (Solved)"
date: 2005-11-09
forum: General Help
---

### Post by bionnaki on 2005-11-09
whever I click a link in thunderbird, it'll open up in firefox, but instead of the actual link, I will be directed to [www.whatyouseek.com](www.whatyouseek.com)

anybody know how to fix this?

thanks

---

### Post by Michael Matthews on 2005-11-09
This is a known bug in thunderbird. It is in their bug reports. Who knows why they don't fix it.

Workaround:
Drag link using left mouse button to url field.

---

### Post by aysiu on 2005-11-09
Is whatyouseek.com your home page? If so, [this thread](http://www.ubuntuforums.org/showthread.php?t=60427) may help you out.

---

### Post by Dr. Nick on 2005-11-09
Mine works fine.

It doesnt open in the same window though, not a big deal.

If you go to  System-Prefrences-Preferred Applications Web Browser tab what is the command for the browser? I think it needs to be  ```
mozilla-firefox %s
``` to work right.

---

### Post by bionnaki on 2005-11-10
[QUOTE=aysiu]Is whatyouseek.com your home page? If so, [this thread](http://www.ubuntuforums.org/showthread.php?t=60427) may help you out.[/QUOTE]

nope. about:blank is my homepage

---

### Post by bionnaki on 2005-11-10
[QUOTE=Dr. Nick]Mine works fine.

It doesnt open in the same window though, not a big deal.

If you go to  System-Prefrences-Preferred Applications Web Browser tab what is the command for the browser? I think it needs to be  ```
mozilla-firefox %s
``` to work right.[/QUOTE]

yes, I have that set...well actually it is set as 
firefox %u & thunderbird is my preferred email client.

if I click a link in TB, firefox will come up, but
[www.whatyouseek.com](www.whatyouseek.com) will be the page instead of the real page...for some reason.

---

### Post by bionnaki on 2005-11-10
[QUOTE=Michael Matthews]This is a known bug in thunderbird. It is in their bug reports. Who knows why they don't fix it.

Workaround:
Drag link using left mouse button to url field.[/QUOTE]

do you know if TB 1.5 RC1 has this bug fixed?

---

### Post by Dr. Nick on 2005-11-10
[QUOTE=bionnaki]yes, I have that set...well actually it is set as 
firefox %u & thunderbird is my preferred email client.

if I click a link in TB, firefox will come up, but
[www.whatyouseek.com](www.whatyouseek.com) will be the page instead of the real page...for some reason.[/QUOTE]

Hmm did you change it to %s and see how it worked?, I set mine to %u and the clicking a tb link opened ff but not to the right page, just said looking up %u and never went anywhere

---

### Post by bionnaki on 2005-11-10
that worked! thanks :D

---

