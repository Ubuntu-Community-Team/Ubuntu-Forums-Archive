---
title: "fluxbox transparency background issue"
date: 2008-08-03
forum: General Help
---

### Post by justinhj on 2008-08-03
Hi 

I followed the steps here to get transparent windows working in fluxbox. 

[http://fluxbox-wiki.org/index.php/Transparency]("http://fluxbox-wiki.org/index.php/Transparency")


Everything works, including shadows and transparency, when i run xcompmgr, except the background goes black. I cannot set a background image with fbsetbg or xli. 

The only error I see in xorg's log is ...

(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)



any ideas appreciated.

---

### Post by justinhj on 2008-08-04
I did try for a long time to google for this before I posted. Honest.

Alas right away I found the solution soon after...

The simple answer is to install feh. 

fbsetbg -i

should tell you if you will have the problem i did.

---

