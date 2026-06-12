---
title: "Grub Error 22 - Can't Find /boot/grub"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Penguin Guy on 2009-04-15
The situation is: I created two Ubuntu systems and then deleted one. When I rebooted this error message appeared on the screen:

```
GRUB Loading Stage 1.5

GRUB Loading, Please wait...
ERROR 22
```

To fix this error you must restore GRUB; see the [[COLOR="Blue"]official Ubuntu guide on restoring GRUB[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by Penguin Guy on 2009-04-15
Bump.

---

### Post by ronparent on 2009-04-15
It appears that you have the solution! Use the code you displayed in your first post with setup (hd0) to restore your grub.

Only guessing, but you probably deleted the grub installed in the partition you deleted. If that is the case, you merely have to run the code to redirect grub to its current location.

---

### Post by Penguin Guy on 2009-04-15
Thanks, I just wasn't sure if I was supposed to install grub on my MBR ([COLOR="DimGray"]setup (hd0)[/COLOR]) or on my Linux partition ([COLOR="DimGray"]setup (hdx,y)[/COLOR]).

Edit: I have found some [[COLOR="Blue"]official Ubuntu documentation that answers my question[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

