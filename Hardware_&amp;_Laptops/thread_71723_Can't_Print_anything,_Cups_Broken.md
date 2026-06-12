---
title: "Can't Print anything, Cups Broken"
date: 2005-10-04
forum: Hardware &amp; Laptops
---

### Post by metalox on 2005-10-04
Since the latest Hoary update no applications can connect to CUPS so I can't print anything. The Gnome Printer administration program (System, Administration, Printing) won't even start. Bad news :(  I have no idea why, so any help much appreciated. I have re-installed cups, but no change. When I try to restart cupsys I get the following error:

$ ben@alonso:~$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd
/usr/sbin/cupsd: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory

That can't be right can it?

---

### Post by metalox on 2005-10-04
Problem Solved! Solution In case anyone else has this problem:

I used synaptic to search for and reinstall the problem library files:
Reinstall:  libcups
Restart cups (sudo /etc/init.d/cupsys restart)
Error: libpaper.so.1
Reinstall: libpaper1
Restart cups (sudo /etc/init.d/cupsys restart)

Now it works. I don't know why but it may be of interest to someone. This would be a real headache for a newbie...

---

### Post by cowlip on 2005-11-03
Thanks this helped fix my problem with Opera

---

