---
title: "GTK problem with linuxdcpp"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by chitresh4u on 2009-01-14
I have started to face some problems with linuxdcpp. Running from shell gives the following output:

> (linuxdcpp:8398): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(linuxdcpp:8398): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

(linuxdcpp:8398): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

and it goes on... like this till I kill the program.. 

Linuxdcpp was working perfectly fine till 2-3 days ago.

---

### Post by sonicb00m on 2009-01-14
There are only harmless code warnings. Is there a switch you can pass to the program to suppress them? It's likely some update to the GTK libraries has caused these messages to appear. As long as the program is running fine I don't think it's a problem.

I usually run it from the icon once I've compiled and installed it so I don't worry about them :D

---

### Post by chitresh4u on 2009-01-14
hi sonicb00m,

actually I forgot to add that the program is not responding ..
I am stuck :(

---

### Post by chitresh4u on 2009-01-15
Update: I figured out that after deleting the settings folder (~/.dc++), linuxdcpp started to work fine. But after hashing the data and connecting to hub it became too slow to use and started to give the same GTK warning again.

I found an alternate solution, using wine to run the windows application (I had DC++ installed on my windows partition). As of now its working great.

---

### Post by diaconescu.stefanandrei on 2009-02-22
Hello,

I have the same problem; linuxdcpp was working fine untill today when I started having the problems:
- the console eror which kept repeating:
"
(linuxdcpp:6452): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
"
 - the program is not responding;
 - when i delete the .dc++ dr from home folder, it works again, but after adding hubs, sharing, and finished hashing i have the same problem.
 - linuxdcpp was working fine before

thank you for any help.

---

### Post by janne_oksanen on 2009-03-11
I have this same problem too. Any ideas?

---

### Post by janne_oksanen on 2009-03-11
I found the bug report for this one and it seems to have been fixed over 6 months ago.

[https://bugs.launchpad.net/linuxdcpp/+bug/256236]("https://bugs.launchpad.net/linuxdcpp/+bug/256236")

I found a work-around that works for me. If I don't automatically connect to hubs when I start the app I can get it running. You can do that by manually editing your favorite hub options.

In ~/.dc++/Favorites.xml change all the Connect="1" to 0.

Hope this helps.

---

### Post by glord2005 on 2009-05-27
[SIZE=2] I had the same prob  but whatever 'janne_oksanen'  told in the above reply helped.
Thanx :D[/SIZE]

---

