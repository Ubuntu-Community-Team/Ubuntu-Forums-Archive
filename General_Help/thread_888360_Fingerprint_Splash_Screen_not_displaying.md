---
title: "Fingerprint Splash Screen not displaying"
date: 2008-08-13
forum: General Help
---

### Post by diggity801 on 2008-08-13
Hi Everyone,

I recently installed Ubuntu on my laptop so I am very newbish. Well I wanted to customize it a bit so I went to Gnome-look.org and downloaded the popular fingerprint loading splash screen. I followed the instructions to install it but it isn't working. I am fairly certain it is because my video card is an ATI mobile xsomething. Is there anything I can add to the grub boot because the vga=971 command (or whatever it is, i forget the number). Anything that might make it actually display on my laptop? Right now it just shows some crazy error screen while loading because it can't display it.

---

### Post by sammael666 on 2008-10-04
had the same problem, found the answer here

[http://ubuntuforums.org/archive/index.php/t-741325.html](http://ubuntuforums.org/archive/index.php/t-741325.html)

specifically, it's changing the resolution in /etc/usplash.conf

---

### Post by sayakb on 2008-10-04
Download the .so file. Install **startupmanager**
Open System->Administration->Startup Manager, set the bootsplash and resolution using the app.

---

