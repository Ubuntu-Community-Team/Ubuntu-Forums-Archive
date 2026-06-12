---
title: "install on Acer TM 8104"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by nielsrondou on 2006-11-02
hi,
when I wanted to install Dapper a few months ago, my screen went blank as soon as the graphical interface appeared.
I solved this problem by CTRL ALT F1 and then in xorg.conf I added Option "MonitorLayout" "LVDS,AUTO", and after that it worked.

Now, I want to install Edgy Eft. When I boot with the CD, the screen goes blank again after a while, but when I press CTRL ALT F1, I don't see a different console, but my screen goes full of purple lines...

somebody knows what can solve this issue? I tried to boot in safe graphics mode but I got the same thing.

thanks, Niels

---

### Post by nielsrondou on 2006-11-04
no one?

---

### Post by Jim Link on 2006-12-21
I have been trying to install linux on mine for 2 days now... no suck luck.  I get the same purple lines you describe with both Ubuntu and Kubuntu (both 6.10).  I tried Fedora core 6 but it just stalls.

Any help would be appreicated... I really want to abandon Microsoft!

---

### Post by Jim Link on 2006-12-22
Well I actually got this working so far so good.  The processor reads out at 2000mhz so that correct and the battery still lasts over 2 hours so thats good too.

what I did was used the command line installer and typed in:

live vga=771

this allowed me to see the gui installer perfectly. Once it was installed I was able to complete the mods necassary to finish my install... Thing works damn near perfectly now.

---

