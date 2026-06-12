---
title: "Cannot Choose Video Card Driver"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by ankitR on 2008-03-24
hi,

I installed gutsy about a week ago on my old Toshiba A10 laptop and its running pretty well -> native res. for the laptop monitor is 1024x768, which it used to run at with the Intel Experimental Driver

However, recently I started to fiddle around with trying to get dual displays and things have gone sour. For some reason, I cannot restore my monitor back to its original resolution, which is now maxed out at 600x800 under the VESA driver; no matter what I do under the "Screens and Graphics" manager, everytime I log in I have the VESA driver selected as default.

All I want to do now is restore my res. to what it was before. FYI its Intel Integrated Graphics 852 GM memory that I have now

any ideas?

---

### Post by elpichi on 2008-03-24
you can use the command

```
 dpkg-reconfigure xserver-xorg
```

to configure which video card and driver to use.

this should also set the resolutions automatic, 
in case it doesn't give you all the resolutions your computer supports
you can change your xorg.conf file under: /etc/X11/xorg.conf to the correct resolutions.

*looking for a good guide for you right now*
EDIT: [http://ubuntuforums.org/archive/index.php/t-544656.html](http://ubuntuforums.org/archive/index.php/t-544656.html)
they pretty much cover how to add resolutions to your xorg file =]

---

