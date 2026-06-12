---
title: "Problem when cleaning Grub Boot Menu"
date: 2008-07-23
forum: General Help
---

### Post by Paul Earland on 2008-07-23
Hello.
After using the command gsku gedit/boot/grub/menu.lst the Run Application appears, I pres Run and a box appears asking for Password. I enter this, and that is the end, the file does not open and nothing is on my screen! Tried this a few times and always the same result.
Thanks.
Paul

---

### Post by ookamisan on 2008-07-23
Have you tried ```
gksu gedit
``` and then browsing to the file /boot/grub/menu.lst via the "open file"-file menu entry?

---

### Post by pauper on 2008-07-23
Perhaps because of typos.

gs[color=red]k[/color]u gedit/boot/grub/menu.lst
g[color=red]k[/color]su gedit[color=red]_[/color]/boot/grub/menu.lst

[Edit:] Make sure you have a single space after "gedit". [color=red]*Don't*[/color] copy&paste
it because I've used underscore to make it more obvious.

---

### Post by Paul Earland on 2008-07-23
> **pauper said:**
> Perhaps because of typos.

gs[color=red]k[/color]u gedit/boot/grub/menu.lst
g[color=red]k[/color]su gedit /boot/grub/menu.lst

Sorry it was just a typo in my question. I have been using gksu gedit.
Just tried again after entering my password screen goes blank.
Paul

---

### Post by jocko on 2008-07-23
> **Paul Earland said:**
> Sorry it was just a typo in my question. I have been using gksu gedit.
Just tried again after entering my password screen goes blank.
Paul

I hope you mean there were TWO typos in your question.
There should be a space between the command (gedit) and the file you wish it to open (/boot/grub/menu.lst).

---

### Post by eentonig on 2008-07-23
My first action when I experience some random strangeness....What do you see when you run the command from a terminal?

---

### Post by jocko on 2008-07-23
> **eentonig said:**
> My first action when I experience some random strangeness....What do you see when you run the command from a terminal?

If he runs the command with gksu, he will not see any terminal output, but if he would use sudo instead, he would see a "command not found" if the problem is what I think (see my post above).

---

### Post by bapoumba on 2008-07-23
> **Paul Earland said:**
> Hello.
After using the command gsku gedit/boot/grub/menu.lst the Run Application appears, I pres Run and a box appears asking for Password. I enter this, and that is the end, the file does not open and nothing is on my screen! Tried this a few times and always the same result.
Thanks.
Paul

Are you trying with the <alt><F2> command prompt ?
Please use the terminal (> Accessories > Terminal) and enter:
```
gksu gedit /boot/grub/menu.lst
```
Give you user password.

---

### Post by Paul Earland on 2008-07-23
> **pauper said:**
> Perhaps because of typos.

gs[color=red]k[/color]u gedit/boot/grub/menu.lst
g[color=red]k[/color]su gedit[color=red]_[/color]/boot/grub/menu.lst

[Edit:] Make sure you have a single space after "gedit". [color=red]*Don't*[/color] copy&paste
it because I've used underscore to make it more obvious.

Thanks to everyone who came back to me.
Yes silly me had not put the "space" in after gedit!
Thanks.
Paul

---

