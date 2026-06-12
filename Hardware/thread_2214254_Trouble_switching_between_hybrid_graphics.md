---
title: "Trouble switching between hybrid graphics"
date: 2014-03-31
forum: Hardware
---

### Post by HonorableGoat on 2014-03-31
I hope I have the right forum here.  I have a Dell Inspiron 5537 with hybrid graphics, which is all well and good.

I've had an off and on relationship with Linux and I figured with the new LTS release coming out I'll put it back on and go from there.  I currently have 13.10 x64 installed and I have to use the Beta drivers from the AMD website as the proprietary drivers from the Updates section in Ubuntu don't support my card.  Alternatively the non-beta drivers from the website don't support 13.10.

When I switch between graphics from AMD -> Intel or Intel -> AMD I occasionally run into problems with X going into low graphics mode and dropping to terminal.  When this happens I need to use the --uninstall switch and then reinstall the graphics drivers.  

Does anyone else experience this issue? 

Also, is there a difference between running ```
 amdconfig --initial 
``` or ```
aticonfig --initial
```

---

### Post by grahammechanical on 2014-03-31
I found these two links

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

Regards

---

