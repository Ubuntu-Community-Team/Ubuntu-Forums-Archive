---
title: "Recycle Bin"
date: 2008-10-09
forum: General Help
---

### Post by Ameya Koshti on 2008-10-09
Hi,
   I am facing this weird problem with ubuntu recycle bin.
There is a folder in the bin "ameya" inside that folder there is 1 folder "desktop" and again inside that folder there is another folder "ameya" and so on(countless!!)...

it tell me that there are 578 files...!! 

and when i click on empty trash it gives me an error sayin " directory not empty"

m uploading some screen shot.

Can some1 please help me out with this?    :confused:

---

### Post by iaculallad on 2008-10-09
Try to empty it on your terminal: Applications->Accessories->Terminal

```
sudo rm -r ~/.local/share/Trash/files/*
```

---

### Post by Ameya Koshti on 2008-10-09
hey thanks bro it worked....

wanted to ask 1 more question...

when i do killall nautilus
the desktop refreshes but the computer browser open every time....and i dont want the computer browser open!!

---

### Post by Ameya Koshti on 2008-10-25
surprise no1 is replying here!!

---

