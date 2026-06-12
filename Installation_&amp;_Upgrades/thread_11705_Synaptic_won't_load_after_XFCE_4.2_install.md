---
title: "Synaptic won't load after XFCE 4.2 install"
date: 2005-01-18
forum: Installation &amp; Upgrades
---

### Post by Valavien on 2005-01-18
I recently installed XFCE 4.2 and everything seems to work well except Synaptic is no longer in my menu.  Also when I run program: sudo synaptic nothing happens.  But when I logout - that's when it asks for my password!

Any ideas - I hope this is the correct area of the forum to ask this.

---

### Post by poofyhairguy on 2005-01-18
[QUOTE=Valavien]I recently installed XFCE 4.2 and everything seems to work well except Synaptic is no longer in my menu.  Also when I run program: sudo synaptic nothing happens.  But when I logout - that's when it asks for my password!

Any ideas - I hope this is the correct area of the forum to ask this.[/QUOTE]


Hmmm. On my Xfce install, its in the system menu (next to the other gnome stuff) is it there?

---

### Post by Valavien on 2005-01-18
I changed repository to Hoary and upgraded synaptic.  However just reinstalling in warty may also work.

---

### Post by dare2dreamer on 2005-01-19
Try adding an item to the menu using gksu instead of sudo.

---

### Post by xalphas on 2005-01-25
hi 

For Synaptic and firestarter like programs to work under Xfce you have to edit the menu file. 

go to /home/usr/.xfce you have to see a file called debian.menu or something like xxx.menu. open with text editor. It is very easy to understand this file. You can change everything.

Forexample for Firestarter you have to add 

+ "&Firestarter" Exec exec gksudo -g /usr/sbin/firestarter

And For Synaptic 

+ "&Synaptic" Exec exec gksudo /usr/sbin/synaptic

And for duplicate menu entries you can delete many lines or add lines like this to this menu file. 

thx.

---

### Post by dejitarob on 2005-02-05
'gksu synaptic' as noted by dare2dreamer works. instead of editing the menu manually, theres a gui editor if you go to settings -> menu editor

---

