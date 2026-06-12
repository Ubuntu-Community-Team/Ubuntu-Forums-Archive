---
title: "keyboard and mouse don't work"
date: 2009-08-10
forum: Hardware
---

### Post by CD4+ on 2009-08-10
hello every, today i tried to install ubuntu on my laptop which is a lenovo y 500. First time when i ran it (from USB stick installation) the keyboard and mouse were working.Then i shut my laptop and reran ubuntu from the memory stick after 2 hrs.To my surprise i find my keyboard and touch pad now not working and so i m not able to use UBUNTU.Please help.

afet rlot of searching i found this :
[http://ubuntuforums.org/showthread.php?t=576323](http://ubuntuforums.org/showthread.php?t=576323)

but i dont know how to rite those lines and where.. please help me..

regards

---

### Post by CD4+ on 2009-08-15
Please can sum1 help.. i really want to throw away windows off my system.. Please help me with the above mentioned post....please  [-o<

regards
CD4+

---

### Post by CD4+ on 2009-08-29
please help...

---

### Post by tsoncul on 2009-09-22
You need to pass the "i8042.reset" line to the kernel at boot. For a live CD or USB, go into the advanced options mode (Tab for USB, I think F6 for CDs) and add that bit after the "boot=" line, so it looks like
```
boot=quiet splash i8042.reset
```

(the exact options may be different, just add i8042.reset to whatever is there)

The keyboard and touchpad should work after that.

Note that you have to do this every time you start your computer. If you do install Ubuntu on this computer, you can add the parameter to the GRUB configuration file so that it's valid for every run.

---

