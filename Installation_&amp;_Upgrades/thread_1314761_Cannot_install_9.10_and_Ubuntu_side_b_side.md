---
title: "Cannot install 9.10 and Ubuntu side b/ side"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by javyn999 on 2009-11-04
Hey all.  I believe I have a messed up partition table.  I did a clean install, installed WinXPSP3, and tried installing Ubuntu 9.10 side by side.  Only problem is, the Ubuntu Partition Manager doesn't see my windows install!  It claims no operating system present. 

Would anyone mind pointing me in the right direction as what to do?  I'd love to do a clean install w/ just Ubuntu, but I need Windows for work apps, and Wine doesn't cut it.  Thanks.

---

### Post by pastalavista on 2009-11-04
Try booting the live CD to the desktop ("try without changes") and use Gparted (partition editor) in the System-> Administration menu. There you can shrink the Windows drive to make space for the Ubuntu installation.

---

### Post by javyn999 on 2009-11-04
Thanks, it worked :)

---

