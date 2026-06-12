---
title: "Serial mouse"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by edmtac2004 on 2005-09-19
serial mouse is not detected during installation...  help please....

---

### Post by franziss on 2005-09-21
i got the same problem here! After finish installing ubuntu, i can't use my mouse! Fedora doesn't give me this problem...

---

### Post by Robertk on 2005-09-22
[QUOTE=edmtac2004]serial mouse is not detected during installation...  help please....[/QUOTE]
 You are talking about hoary, right. Okay, the problem is on installation linux assumes your mouse is connected to your PS/2 port. You can change this by editing a text file.

1. In the login screen press Alt+F1
2. It will then ask you to login, login using name and password used in installation.
3. Use the command "sudo nano /etc/X11/xorg.conf" to open the file that needs to be changed in the text editor. Note CaPiTaLs! (i spent an hour figuring out why it wouldn't open)
4. Scroll down the file to the part Reffering to the mouse, and change device  to "/dev/ttyS0" (That's a zero and remember the capital S)
5. Also change the console to "Microsoft"
6. Press Ctrl+X and save
7. Restart your computer.

By the way, make note of any changes you make so that you can change them back if you stuff things up!

---

