---
title: "Gnomes keyboard selector not working!"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by dgrafix on 2006-02-17
Im trying to change the keyboard layout from english to swedish in gnome.

It dosent seem to want to be swedish, even though it says swedish with a tick and i have removed the US one and rebooted.

my oh aah and errs are all missing!!! :(

---

### Post by zugvogel on 2006-02-17
Try typing "setxkbmap" in the consol and see if everything works. I think the keyboard-switching doesn't work exactly as it should do. Let me know if you have success with this.

---

### Post by Miro on 2006-02-17
I had to do this by editing xorg.conf. This is how I did it:
Option "XkbModel" "pc105"
Option "XkbLayout" "fi"

(Change fi to se, maybe).

---

### Post by dgrafix on 2006-02-18
zugvogel, that line did not seem to change anyything

miro, that worked, it was se

---

### Post by psypher on 2006-02-26
this  [thread]("http://ubuntuforums.org/showthread.php?t=102760&highlight=change+keyboard+layout") where you just add the keyboard indicator to your taskbar worked for me

---

