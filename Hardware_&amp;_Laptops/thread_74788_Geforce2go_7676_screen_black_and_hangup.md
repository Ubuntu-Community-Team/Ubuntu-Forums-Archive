---
title: "Geforce2go 7676 screen black and hangup"
date: 2005-10-12
forum: Hardware &amp; Laptops
---

### Post by tommi on 2005-10-12
Guten Abend (Good evening)

(sry for bad english, german thread is located here: [http://www.ubuntuusers.de/viewtopic.php?t=12516](http://www.ubuntuusers.de/viewtopic.php?t=12516) )

hi ppl, i need your help.

I use breezy in my Toshiba Sattelite 3000-514 with GeForce 2 Go. If i install the Breezy 7676 via apt-get all works but if i shut down the screen blanks (backlight switch off)  and the system hangs.

i tell a little bit more. in hoary i had problems too. with hoary i modified /etc/modules and added following behin nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=2 . without these line, x locks up during loading of X. after this all works but if i switch to console in x screen blanks and sys lock up. during shut down i had graphic erros and cant read in the console.

now with breezy i tried this to, the the laptop goes down correctly but i have the same errors (cant switch to console and during shut down graphic errors) and if screensaver is activated screen blacks (and backlights are off) and i must disconnect power supply.

tested a few days ago. now i want to test other option but nvidia isnt listet in /etc/modules .. from where ist it loaded ? i want to test other options as in [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7676/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7676/README.txt) listed (mobile=0xFFFFF for example) thats the reason why i cant play with the options ... but maybe a peole knows the solution and i can save the time .. we will see ..

---

### Post by valadil on 2005-10-12
I have a dell inspiron with a similar geforce2 go.  I was going to suggest the softedids line you listed, but you already took care of that.  Anyway, the problem is with the nvidia drivers.  They're too new.  You need to downgrade to 6111 or 6106 I think.  You'll also probably need a new kernel.  I think the last one that worked out of the box (or out of the tarball) with 6111 was 2.6.6.  Newer kernels will need more patches applied if you want nvidia drivers to compile with them.  I think I managed to get my laptop working on a 2.6.10 kernel with only one patch.  To find the right kernel patches you'll have to install a kernel, try to install the nvidia driver, and google for kernel patch + whatever error the nvidia driver gave when it failed.

Or you could just ignore 3d acceleration and use vesa drivers.

---

