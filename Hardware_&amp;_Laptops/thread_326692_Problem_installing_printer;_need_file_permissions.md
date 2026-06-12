---
title: "Problem installing printer; need file permissions"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by Dalkantrell on 2006-12-28
I'm trying to install an HP deskjet f330.  I looked this up on the forums and found a previous post.  I downloaded the file listed but, I can't save the file into usr/share/cups/model.  I don't understand what to do.  When I try to drag the file to the location it says, "error while copying to /usr/share/cups/model.  You do not have permission to write to this folder."  I have tried to install things in ubuntu in the past by copying a file to a pre-desribed location and always run into this problem.  I'm totally lost when it comes to ubuntu and don't know what to do.  It gets frustrating very quickly.  Any help would be greatly appreciated.

---

### Post by po0f on 2006-12-28
Dalkantrell,

To drag-and-drop to a directory where you need sudo premission, open a Nautilus window like this (from the terminal):
```
[FONT="Courier New"]$ gksu nautilus[/FONT]
```

---

