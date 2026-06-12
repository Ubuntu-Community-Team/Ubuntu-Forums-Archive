---
title: "Editing xorg.conf and grub2"
date: 2011-06-12
forum: Hardware
---

### Post by garagestmarien on 2011-06-12
First, sorry if this is the wrong place to post, but my question relates to my graphics card.
I have tried to add to the xorg.conf file and the grub2 file and while I can open them, I cannot edit them.
I changed my user status to administrator and that has not helped.
I tried writing a new file to replace the one I want altered but this will not work either.
So, how do I edit these files?

---

### Post by coffeecat on 2011-06-12
Your thread is tagged "solved" yet mine is the first reply. Have you solved your issue? If so, please post again to confirm this. Or you might want to remove the solved tag if you have not so that people are not put off from reading the thread.

Anyway. To edit xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```If you want help editing the grub configuration post back with what you want to do. If you are trying to edit grub.cfg, then it's best you don't. Not that you'll have much luck with its default permissions anyway. Re-configuring grub is a bit more involved.

---

### Post by garagestmarien on 2011-06-12
Yes, I have solved the issue.
However, I did it a different way to your suggestion.
Whether this is the right or wrong or just another way, it worked very well for me.
I used the following command (and have added others, if it helps anyone else)



If you're using **Ubuntu (Gnome)**, press Alt-F2 and type 
gksudo nautilus


  If you're using **Kubuntu (KDE)**, press Alt-F2 and type 
kdesu konqueror


  If you're using **Xubuntu (XFCE)**, press Alt-F2 and type 
gksudo thunar

---

