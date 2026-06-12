---
title: "Corsair Strafe RGB still not working on ubnutu 15.10"
date: 2016-05-12
forum: Hardware
---

### Post by lucas60 on 2016-05-12
Hello everyone,

a couple weeks ago I got a new keyboard, the Corsair Strafe RGB, and around the same time I decided to install ubuntu 15.10 (again). Now at first everything seemed to work just fine, but a few days ago my keyboard just kind of stopped working. At start it sais "usb_submit_urb(ctrl) failed: -1" and I know that this is a very well known problem and there is a rather simple solution online. Basically you have to insert "usbhid.quirks=0x1B1C:0x1B12:0x20000000" (its a different code for the strafe rgb but its just a demonstration) to your GRUB_CMDLINE_LINUX_DEFAULT (btw I did reloaded GRUB and reboot etc. I made sure to do exactly as described). Sadly that seems to work for everybody but me. I really hope anyone can help me out on this one because I'm starting to get desperate, even thought about installing windows... already thanks in advance.

Sincerely yours,
Lucas

//some information I forgot the first time: the message stopped appearing on boot, but it still doesn't take my input. Ironically the lighting works just fine...

---

### Post by lucas60 on 2016-05-14
Okay since I know many people have this problem, I just really quick wanted to tell you that I found the most stupid workaround EVER. And its working very well. So after I had all these problems, I reinstalled my Ubuntu a couple of times, different versions, the "nomodset" flag and everything, but I didn't get it to work. So because I was angry I just spammed my Super key while booting Ubuntu and suddenly my keyboard worked. I thought that I might have been lucky but I tested it like 20 times (also on different machines) and it works! And I know its super stupid but I hope this helps anyone else (I don't know if other keys will work, didn't test that). So like I just spam click the key from the moment the error shows up while booting till I see the Ubuntu desktop like once a second. Still cant believe it...

//So far i tested it on 15.04, 15.10 and 16.04 all wored just fine
//And btw can somebody tell me why this is working, I'm dying to know

---

