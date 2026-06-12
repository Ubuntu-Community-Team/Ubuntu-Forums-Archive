---
title: "Xfce and cairo - black box behind dock?"
date: 2008-11-17
forum: General Help
---

### Post by lunar cranium on 2008-11-17
I am having issues with my cairo-dock on my xubuntu desktop environment.  The dock works flawlessly in Gnome, but i prefer the speed that Xfce provides on loading.  I have compiz enabled on the machine, and have run compiz-check.  these are the results:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   Xfce
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...grep: /home/kyle/.config/xfce4/mcs_settings/wmtweaks.xml: No such file or directory
           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you won't be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) n

```

here's what it looks like on the desktop.
[IMG]http://i36.tinypic.com/efjh8h.png[/IMG]

any ideas what's going on?  when in Gnome it didn't return that error.

---

### Post by lunar cranium on 2008-11-17
this is what i get on the same machine in the Gnome desktop environment.

```
kyle@OP:~$ compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you won't be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) n
kyle@OP:~$ 

```

[[IMG]http://img99.imageshack.us/img99/3710/s1ie6.th.jpg[/IMG]](http://img99.imageshack.us/my.php?image=s1ie6.jpg)[[IMG]http://img99.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by myddewji13 on 2008-11-17
i dont know about xubuntu...but in ubuntu if you cant run compiz you can enable basic compositing effects in metacity using this tutorial: 
[http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/)

(very simple)

that should fix the black box issue in ubuntu

---

### Post by lunar cranium on 2008-11-18
> **myddewji13 said:**
> i dont know about xubuntu...but in ubuntu if you cant run compiz you can enable basic compositing effects in metacity using this tutorial: 
[http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/](http://tombuntu.com/index.php/2008/11/14/metacity-compositing-effects-in-ubuntu-810/)

(very simple)

that should fix the black box issue in ubuntu

thanks for the reply.  i'll check that out.  but i don't have any problem running compiz in ubuntu.  i'll see what that does for me in xubuntu.

---

