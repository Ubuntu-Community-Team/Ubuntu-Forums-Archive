---
title: "start up"
date: 2008-07-16
forum: General Help
---

### Post by mr.farenheit on 2008-07-16
anyone know any quick was to make ubuntu start up faster?

---

### Post by Arthur Archnix on 2008-07-16
Plenty of threads on the issue already. So I'll just give you one and mention another.

Next time you boot go into grub and edit the boot line. Add at the end of the kernel line "profile" without quotes. So it would look like:
 
kernel=/blah/blah/blah /dev=/blah/blah/blah ro profile

This will only affect this one boot. It will look at what files are needed to boot, what order they are acessed in, then move files around a bit so that they're read quicker. Thus, it will boot a lot slower this one time. When you get to the login manager, don't login, just reboot.

Then lookup sysvconfig.

---

### Post by DJ_Peng on 2008-07-16
There are actually [several]("http://ubuntuforums.org/showthread.php?t=89491") [threads]("http://ubuntuforums.org/showthread.php?t=810514") on these forums addressing this, as well as a [blog article]("http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/") linked to on one of the threads. Not to be mean, but there are several more available that will turn up in a [search]("http://ubuntuforums.org/uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=speed+up+Hardy+boot+time&sa.x=0&sa.y=0&sa=Search#1028") (via Uboontu.com, a great Ubuntu-specific search tool), which is why several people recommend searching before posting a new question. Chances are pretty good that any question you have may have been posted already, and there may be solutions for the issues posted already.

---

