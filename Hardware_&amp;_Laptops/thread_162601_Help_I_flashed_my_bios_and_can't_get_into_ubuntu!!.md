---
title: "Help I flashed my bios and can't get into ubuntu!!!"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by lagerman on 2006-04-19
I have a gateway solo 1450 and saw on there website that there is a bios update so I did it and now I can't get into ubuntu:(  It says the updated bios is for the VGA bios and I don't know how to configure X server. Any help would be great.

---

### Post by krusbjorn on 2006-04-19
try "sudo dpkg-reconfigure xserver-xorg".

---

### Post by lagerman on 2006-04-19
Tried that still dosen't work.


I get this error message when I try to start x:

(EE) I810(0): No video bios modes for chosen depth
(EE) Screen(s) found, but none have usable configuration


Fatal error
No screens

---

### Post by lagerman on 2006-04-27
update: this is the error that I get after I tried to reconfigure my xserver:

Skipping "usr/X11R6/lib/modules/extensions/libGLCore.a:m_debug_clip.o": no symbols found
Skipping "usr/X11R6/lib/modules/extensions/libGLCore.a:m_debug_norm.o": no symbols found
Skipping "usr/X11R6/lib/modules/extensions/libGLCore.a:m_debug_xform.o": no symbols found

(EE)I810(0) No video BIOS modes for chosen depth
(EE)Screen(s) Found, But none have a useable configuration

Fatal Servver Error:
No screens found


Some body please help me. Or do I have to format and start all over again. Which really isn't that much of problem. But if I don't have to do it I won't :)

---

### Post by Lord_Arithon on 2006-04-27
Well here is the problem when you flash your bios.  If you do something wrong you are basically up the creek without a boat.  You may have to go back in and re-flash your bios....but I would do the re-install to see if it works instead.

I hope you backed up all your information.

Aaron

---

### Post by lagerman on 2006-06-16
Update I reflashed my bios with an older version that I found on the internet. And did a reinstall and am happily back using ubuntu :)

---

