---
title: "Possible to have conky overlay float on top?"
date: 2008-11-06
forum: General Help
---

### Post by anystupidname on 2008-11-06
I would like my conky information to "float" on top of everything. Is this possible and if yes, could somebody please point me to a howto?

Thanks!

---

### Post by cammin on 2008-11-06
find a line that says
**own_window_type**
and make  sure it says
**own_window_type normal**

then find
**own_window_hints**
and make sure it says
**own_window_hints undecorated,above,sticky,skip_taskbar,skip_pager**

**undecortated** means it has no borders or title bar
**sticky** means it stays on all desktops
**skip_taskbar** keeps it from showing up on the taskbar
**skip_pager** keep you from selecting it with alt+tab

---

### Post by EXCiD3 on 2008-11-06
cammin forgot to mention that 'above' means it stays on top of everything :P

---

### Post by m_l17 on 2008-11-06
Take a look at this guide if you want to do more with conky:

[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/]("http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/")

And these threads:

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")

[http://ubuntuforums.org/showthread.php?t=205865&highlight=conky]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky")

---

### Post by anystupidname on 2008-11-06
@cammin: That is almost what I wanted but I (incorrectly?) assumed I would be able to operate windows under it. Instead, the conky stats prevent access to windows under them. Do you understand what I mean? Is it possible to do that or will that area of the desktop be unusable as long as the stats are floating above other windows?

@everybody: Thanks for the info. I appreciate it.

---

### Post by cammin on 2008-11-06
As far as I know, you can't access the parts of windows covered by the conky window with the mouse.
One option is to remove **undecorated** from the **own_window_hints**. Then rolling up the window when you want access underneath it. If you don't want to roll the window up, you can remove the **skip_taskbar** and/or **skip_pager** options and use the taskbar or alt+tab to bring the window back up.

---

