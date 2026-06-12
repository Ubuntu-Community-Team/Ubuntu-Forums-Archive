---
title: "Kubuntu-&gt;Ubuntu w/o reinstall"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by el3ktro on 2006-01-31
I have running Kubuntu on my iBook, but I recently switched to Ubuntu on my desktop machine by reinstalling it, but now I also want to switch to Ubuntu on the iBook. Because my girlfriend also uses this, I want to have a second user account for me with Gnome, and keep the current user account for my gf with KDE. As far as I know I can just install ubuntu-desktop, which would install all the Gnome stuff. I've heart in this forum that a parallel install of KDE + Gnome can mess up the applications menu, is that true? Also, I'd like to have the Ubuntu bootsplash instead of the Kubuntu one, is that possible? Oh, and also I'd like to use gdm instead of kdm (looks much nicer), can I just remove kdm and install gdm to do that? Are there any other things i should be aware off?

Thanks for your help!
Tom

---

### Post by stuporglue on 2006-01-31
I haven't had any problems with both installed. Some extra menu items, yes, but nothing broken. If you're installing Ubuntu second, I'll think it'll replace the splash and KDM.

---

### Post by el3ktro on 2006-01-31
Okay another question. There was only ONE user on the iBook, the home dir was just /home (NOT /home/$user). Is it save to usermod this user so the new home is /home/karin (my gf) and move all files to the according dir, so that i can create another user account for me with /home/tom as home dir? When KDE correctly uses ~ instead of /home in all paths there shouldn't be a problem right?

Tom

---

### Post by Adrian on 2006-01-31
[QUOTE=el3ktro]As far as I know I can just install ubuntu-desktop, which would install all the Gnome stuff. I've heart in this forum that a parallel install of KDE + Gnome can mess up the applications menu, is that true?[/QUOTE]

I've seen people reporting different kind of errors. I've been lucky though. However, you're KDE applications will show up in the Gnome menu and vice versa. You can edit the menus by hand, and delete the programs you don't want to use in each DE manually. You can also do it automatically, as described here: [http://www.ubuntuforums.org/showthread.php?t=59455](http://www.ubuntuforums.org/showthread.php?t=59455)

>  Also, I'd like to have the Ubuntu bootsplash instead of the Kubuntu one, is that possible? 

Check out this thread: [http://www.ubuntuforums.org/showthread.php?t=113250](http://www.ubuntuforums.org/showthread.php?t=113250)

>  Oh, and also I'd like to use gdm instead of kdm (looks much nicer), can I just remove kdm and install gdm to do that? Are there any other things i should be aware off? 

Doing this:
```
dpkg-reconfigure gdm
```
should let you choose gdm instead.

---

