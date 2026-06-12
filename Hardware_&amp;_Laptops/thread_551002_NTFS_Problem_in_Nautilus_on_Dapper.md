---
title: "NTFS Problem in Nautilus on Dapper"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by zolero on 2007-09-14
Hi there.

Recently - upon some messy tries with Feisty and Gutsy Tribe 5 - I've switched back to Dapper (ver. 6.06.1) with server kernel.
Currently I've installed NTFS-3G with read/write support upon some howtos instructions. Initially it was complaining about some dependencies, but I've resolved them by installing the needed packages from Feisty.
Now everything works well with the NTFS partition. It mounts automatically at boot as is stated in my FSTAB. I can read and write it perfectly, but Nautilus didn't shows it up on its sidebar or on the desktop. Thus I can't browse it directly, and this issue bothers me. Here are some shots about relevant issues related to this. Can anyone help me with this, plz?

[http://img237.imageshack.us/img237/9844/fstabut6.png](http://img237.imageshack.us/img237/9844/fstabut6.png)
[http://img237.imageshack.us/img237/4853/desktopshotvv0.png](http://img237.imageshack.us/img237/4853/desktopshotvv0.png)
[http://img237.imageshack.us/img237/6365/nautilusshot1jw7.png](http://img237.imageshack.us/img237/6365/nautilusshot1jw7.png)
[http://img237.imageshack.us/img237/28/nautilusshot2tm3.png](http://img237.imageshack.us/img237/28/nautilusshot2tm3.png)

Thanks in advance.

---

### Post by Blastomorpha on 2008-03-05
I've just installed ntfs-g3 in Dapper right now and i have the same problem: I can enable both internal and external drive support, but once did I can't access them via Nautilus, only via terminal.
For example, before running ntfs-config, I have a "LACIE" icon (shortcut to my usb drive partitioned with ntfs) on my desktop. After that, the icon disappears, and I have to go in /media/LACIE to use it.
If I try to double-click on the "LACIE" icon in "Resources" window (sorry, I'm italian so I don't know if it's right) I get this message: > error: device /dev/sda1 is already mounted to /media/lacie
error: could not execute pmount

---

### Post by Blastomorpha on 2008-03-05
It solved itself! :confused:

---

