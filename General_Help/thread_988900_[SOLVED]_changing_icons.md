---
title: "[SOLVED] changing icons"
date: 2008-11-21
forum: General Help
---

### Post by trendyabinash on 2008-11-21
Sir I am not able to change my icons.

In one of the forum I have read that by going to system-->appearances-->customise-->icons and dragging there the icon package that I have downloaded. but due to some reason it is not working whenever i drag a package to icons it returns to it's original position.

I tried to extract the files and then copy them to the /usr/share/icons folder but it is saying access denied. Why is it so? I am the administrator after all.

how can I install these packages?[black and white is the icon package]("http://www.opendesktop.org/content/show.php/black-white+2+Neon?content=72620")

---

### Post by IceReaver75 on 2008-11-21
As far as I know you have to have be root to make any canges you your /user/share folders.  If you have the icons extracted to a folder you can try typing 

sudo nautilus 

into a terminal and then navigate to your user/share/icons folder and try to drag the icon folder that way.  It should let you.

never mind that there is the black-white_2-Neon.tar.gz in the extracted folder install that file through the appearance setting like any other icon install and should install for you that way.  I just took a look at the file myself.

---

### Post by kostkon on 2008-11-21
You can simply extract it in your .icons folder, i.e.
```
~/.icons
```

---

### Post by trendyabinash on 2008-11-21
> **kostkon said:**
> You can simply extract it in your .icons folder, i.e.
```
~/.icons
```
thanks this trick worked

---

