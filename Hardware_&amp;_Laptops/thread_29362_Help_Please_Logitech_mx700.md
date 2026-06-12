---
title: "Help Please Logitech mx700"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by KezzerDrix on 2005-04-24
How do I install all my mx700 so that I can have easy access to all its buttons?

---

### Post by rotorwash on 2005-04-24
[QUOTE=KezzerDrix]How do I install all my mx700 so that I can have easy access to all its buttons?[/QUOTE]
Try [here](http://www.linux-gamers.net/modules/wfsection/print.php?articleid=46)

---

### Post by Mat10 on 2005-04-24
Hey Rotorwash, would ya happen to be an old chopper vet ?


Tom                 \\:D/  \\:D/

---

### Post by Firetech on 2005-04-24
[QUOTE=rotorwash]Try [here](http://www.linux-gamers.net/modules/wfsection/print.php?articleid=46)[/QUOTE]
 That guide works, but you should ignore the first step (patching and checking the X-binary) when running in ubuntu.
Note that there may be some problems with the fast scroll up button (the one in front of the scrolling wheel, away from you) may trigger a "go back action". If this happens, try moving the mouse from USB to PS/2. (This solved the problem for me, but I have a Cordless Optical Desktop MX.)
Also, you don't need the 10 button setting. Just set "Buttons" to "7" and "ZAxisMapping" to "4 5".

---

### Post by rotorwash on 2005-04-24
[QUOTE=Mat10]Hey Rotorwash, would ya happen to be an old chopper vet ?


Tom                 \\:D/  \\:D/[/QUOTE]

I am an old vet but fairly new to choppers  :)

---

### Post by BiGx5MurF on 2005-04-25
I've tried using that guide, but even when using the root terminal, when I try to edit the xfree86 config, I get the message "bash: /etc/X11/xorg.conf: Permission denied"
or
"bash: /etc/X11/XF86Config: No such file or directory"


Can anyone help me get my extra mouse buttons working? I have a logitech mx700

---

### Post by Firetech on 2005-04-26
[QUOTE=BiGx5MurF]I've tried using that guide, but even when using the root terminal, when I try to edit the xfree86 config, I get the message "bash: /etc/X11/xorg.conf: Permission denied"
or
"bash: /etc/X11/XF86Config: No such file or directory"


Can anyone help me get my extra mouse buttons working? I have a logitech mx700[/QUOTE]
 You have to be root to edit the config (run it from a console or run dialog and prefix the command with "sudo ", like "sudo gedit /etc/X11/xorg.conf")

---

### Post by Firetech on 2005-04-26
[QUOTE=BiGx5MurF]I've tried using that guide, but even when using the root terminal, when I try to edit the xfree86 config, I get the message "bash: /etc/X11/xorg.conf: Permission denied"
or
"bash: /etc/X11/XF86Config: No such file or directory"


Can anyone help me get my extra mouse buttons working? I have a logitech mx700[/QUOTE]
 The config file is not an executable.
Start the root terminal and run "gedit /etc/X11/xorg.conf".

---

### Post by cmsj on 2005-08-10
[QUOTE=][/QUOTE]
 I have written [http://docs.tenshu.net/Logitech-MX-Duo-mini-HOWTO/](http://docs.tenshu.net/Logitech-MX-Duo-mini-HOWTO/) which may be of use.

---

