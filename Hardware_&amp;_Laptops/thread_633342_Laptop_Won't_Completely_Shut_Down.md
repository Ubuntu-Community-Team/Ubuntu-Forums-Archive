---
title: "Laptop Won't Completely Shut Down"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by teejay17 on 2007-12-06
Since installing Ubuntu 7.10, my laptop won't completely shut down. Instead, it will show the Ubuntu splash screen in perpetuity, until I physically turn the computer off. 
Would anyone know how to fix this problem?

---

### Post by teejay17 on 2007-12-07
Since installing Ubuntu 7.10, my laptop won't completely shut down. Instead, it will show the Ubuntu splash screen in perpetuity, until I physically turn the computer off. 
Would anyone know how to fix this problem?

---

### Post by aquavitae on 2007-12-07
What does it show on a different terminal (press Ctrl-F1 to switch to tty1, Ctrl-F2 for tty2, etc)?  One of them, I think its tty2 (Ctrl-F2) should show a log of what's happening.  If there's an error you'll see it there.  That might help.  Alternately, when you start up, edit the grub command (I think you press e or c in the grub menu, it should say at the bottom of the screen), and remove the command 'splash'.  When you shut down it should then show a listing of what its doing.

---

### Post by teejay17 on 2007-12-08
> **aquavitae said:**
> What does it show on a different terminal (press Ctrl-F1 to switch to tty1, Ctrl-F2 for tty2, etc)?  One of them, I think its tty2 (Ctrl-F2) should show a log of what's happening.  If there's an error you'll see it there.  That might help.  Alternately, when you start up, edit the grub command (I think you press e or c in the grub menu, it should say at the bottom of the screen), and remove the command 'splash'.  When you shut down it should then show a listing of what its doing.
It's not so much a problem with the splash screen, as it is the hardware itself. The machine completely shuts itself down, with only the monitor and a "Ubuntu" splash screen displayed on it. 
The best comparison I can make is that of the old Windows 95 PCs, where it told you "It is now safe to turn of your computer." That's the same thing that's happening with me...only it's Ubuntu 7.10.

---

### Post by aquavitae on 2007-12-10
The idea is that if you hide the splash screen you might see an error message that would tell you what the problem is. E.g. 'Error: Cannot kill display'

---

