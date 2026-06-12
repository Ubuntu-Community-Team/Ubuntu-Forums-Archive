---
title: "[SOLVED] Log In Screen Not Working"
date: 2008-08-15
forum: General Help
---

### Post by dethredic on 2008-08-15
So, I was playing around with themes and login screens yesterday, I downloaded on from gnome-look.org and installed it and selected it.

I rebooted and when it would normally show the login screen it just shows that solid colour, and the mouse has the loading sign for like 5 mins and nothing happened. I tried 3 times.

How do I change/fix the login screen via the system restore link in my grub?

---

### Post by dethredic on 2008-08-15
Ok, some more info, I see the nVidia splash screen that comes with the drivers I have installed, that comes before the login window.

Any ideas?

---

### Post by exploder on 2008-08-15
Try hitting cont, alt, backspace to see if you can force the gdm screen to appear.

---

### Post by dethredic on 2008-08-15
I do that and it just takes me to the place where I freeze.

EDIT: Fixed it.

I went to /usr/share/gdm/themes and deleted the bad theme that I had. I then booted up and it gave me an error saying it could not find the file (well duh I deleted them). It then loaded the default login window and I could login. I went admin> login and changed it back to the human one.

---

