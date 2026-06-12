---
title: "Usb devices automounted and autobrowsed - even with gnome-volume-manager disabled"
date: 2008-04-27
forum: Hardware
---

### Post by yurac on 2008-04-27
Hi, 

I run Ubuntu 8.04 final on IBM thinkpad T42.
Each usb device that I connect gets automounted and autobrowsed.
This is annoying for me. I want to disable that. I first disabled automounting and autobrowsing
in gconf volume_manager configuration options. No result.
Then, I removed gnome-volume-manager completely and checked with ps that
it is not running. Still no result. I guess that some other program 
does the automounting but I have no idea which one.

Any ideas?

Thanks

---

### Post by yurac on 2008-04-27
Solved it myself.
Nautilus is the program that automounts all usb devices.
To disable:

gconf-editor => apps -> nautilus -> preferences ->
         uncheck media_automount and media_automount_open


Thanks!

---

