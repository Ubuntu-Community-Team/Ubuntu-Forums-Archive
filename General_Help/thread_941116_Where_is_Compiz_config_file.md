---
title: "Where is Compiz config file"
date: 2008-10-07
forum: General Help
---

### Post by celticbhoy on 2008-10-07
I have just updated my Compiz Fusion to the latest GIT version using a script on the forums. The problem is that it has defaulted to using Emerald, and my system wont run Emerald. Where is the config file to change back from emerald, without having to run Compiz and clicking on the icon ???

---

### Post by celticbhoy on 2008-10-07
OK found it, but its not what I want, it only contains settings for compiz itself. What I need is the config file that tells Ubuntu to use emerald - anyone any ideas?

---

### Post by celticbhoy on 2008-10-08
Bump......

---

### Post by Therion on 2008-10-08
I thought that Emerald was called up by default when Compiz starts?  

You might like this [Fusion Icon](http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/)!  You can use it to select Emerald as your default Window Decorator as well as switch between MetaCity and Compiz.

---

### Post by celticbhoy on 2008-10-08
Sorry might not have made myself clear, The version of fusion is working fine, but after the upgrade it has set Emerald as the window manager. As my graphic capabilities are low my machine wont play with Emerald. I need to set the window decorator back to normal, but when i right click on the compiz icon it does not display the menu on screen so I need a way to reset this option manually without compiz running.

---

### Post by airtonix on 2008-10-09
fire up gconf-editor and hunt around in there

---

### Post by celticbhoy on 2008-10-09
I have had a look in gconf-editor, but I cant find referance anywhere. I dont know if this is becuase I am using KDE when looking (cant use Gnome with my problem). However there must be a config file somewhere which stores this info, and I just hope that someone out there knows where it is.

---

### Post by meho_r on 2008-10-09
Just a hint, not sure if it works. In ccsm there is Window Decorator option. If you look at it you'll see:

gtk-window-decorator --replace

Maybe try to put this command (don't know KDE equivalent, sorry) in you sessions configuration.

---

### Post by celticbhoy on 2008-10-09
What I meant was that I was using KDE as a session as Gnome was autostarting Compiz, removed the autostart line and am back to using gnome again, will try your idea though.

---

