---
title: "cairo-dock update problem."
date: 2008-08-22
forum: General Help
---

### Post by zephyr0911 on 2008-08-22
Hi everybody..I need some help..

My cairo-dock update this morning( version 1.6.2-RC1),after I restart my computer,i notice something wrong with it.So I configure my cairo-dock,when i click applets,all of them disappear!

So...I remove cairo-dock and install it again by SPM.But still wrong.Now I can only choose the default theme and no applets...

Anybody can tell me why?thanks..

---

### Post by fabounet on 2008-08-22
check that the plug-in's package has the same version as the dock's package.
if the version mismatches between the dock and an applet, this one won't be loaded (for security)

---

### Post by zephyr0911 on 2008-08-22
Thank you friend!

I have reinstall the same version of dock and plug-ins.But I still can't see the applets:(

Just like this:
[ATTACH]82511[/ATTACH]

---

### Post by zephyr0911 on 2008-08-24
Please...who can help me...I had try to reinstall the dock(ver.1.6.1.2)...But I still can't choose the applets,just like the image above...I really love the cairo-dock and don't wanna change to another one...:(

---

### Post by fabounet on 2008-08-25
how did you install it ?
try to remove it completely (apt-get --purge, plug-ins too), then reinstall it from a single repository (maybe you mixed 2 repositories)
see the wiki for how to add the cairo-dock's repository to your list.

---

### Post by zephyr0911 on 2008-10-20
Hello...Anybody can help?:(

---

### Post by fabounet on 2008-10-21
remove everything you installed, and then :
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")

---

