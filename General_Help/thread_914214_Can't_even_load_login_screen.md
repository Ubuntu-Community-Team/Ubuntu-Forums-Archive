---
title: "Can't even load login screen"
date: 2008-09-08
forum: General Help
---

### Post by blazemore on 2008-09-08
I thought I'd check out KDE 4.1.1, so I installed kubuntu-kde4-desktop (or whatever it is) on my Ubuntu system.
I set kdm-kde4 as my default window manager.
Now when my system boots up, KDE gives me an error message (something about a greeter, doesnt matter), and when I OK it, I just get a blank screen. Ctrl+alt+backspace doesnt work, neither does Ctrl+Alt+F3 or whatever. I just want to get rid of KDE and kdm completely.

I removed recovery mode from my grub ages ago so I can't even get a command line!

I have autologin enabled, and I'm not sure if this error is coming up as part of the login screen, or after login.

---

### Post by blazemore on 2008-09-08
Does nobody have any idea? I really need this system up for tonight, and while I have a seperate /home partition, I really don't want to reinstall.

---

### Post by S.A.A on 2008-09-08
You make it so hard, but i have an idea:
in the grub splash screen, press "e" and go to the line hat begins with "Kernel" then add this to the end: "vga=normal", then press "enter" then "b" to boot..

---

### Post by S.A.A on 2008-09-08
You make it so hard, but i have an idea:
in the grub splash screen, press "e" and go to the line hat begins with "Kernel" then add this to the end: "vga=normal", then press "enter" then "b" to boot..

---

### Post by blazemore on 2008-09-08
I will try but I don't think it's a display setting. I am going to upgrade to Alpha 5 now anyway, so that will fix the problem (Unless it's a dodgy setting somewhere in /home)

---

