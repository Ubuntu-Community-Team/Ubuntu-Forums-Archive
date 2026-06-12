---
title: "Gnome Terminal - &quot;B&quot; key not working ... ???"
date: 2005-11-30
forum: General Help
---

### Post by vaskark on 2005-11-30
In gnome terminal the 'B' key on my keyboard stopped working. It works fine in other terminals, though. Anyone know how to fix this? Gnome terminal is my fav. Thanks.

---

### Post by akudewan on 2005-12-01
Try running gnome-terminal as a diifferent user, does it work then?

---

### Post by vaskark on 2005-12-01
[quote=akudewan]Try running gnome-terminal as a diifferent user, does it work then?[/quote]
I opened gnome-terminal as root and it does indeed work. So what should I try next?

---

### Post by akudewan on 2005-12-01
Go to Terminal>Set character encoding and see what is selected. I have *Current Locale (UTF 8)* selected

If that doesn't work, try deleting your profile and creating a new profile. Maybe the "B" key was set as a shortcut, you could also look in Edit>Keyboard shortcuts

---

### Post by vaskark on 2005-12-01
Thanks. Turns out that the "B" key was set as a keyboard shortcut, although I don't know how that happened.

Thanks for your help ;)

---

### Post by liam_stoush on 2006-11-27
I had the same problem with Gnome Terminal and the "t" key after doing an upgrade through apt-get.
Sure enough the letter had been set as a shortcut. Very odd.

---

