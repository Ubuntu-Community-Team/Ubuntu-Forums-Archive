---
title: "Lost Space?"
date: 2008-08-27
forum: General Help
---

### Post by Zhane on 2008-08-27
I've a problem here... it seems that even after I deleted a file and empty the trash.. and restarted, the file that I've 'deleted' is still taking up the space on my usr.disk although it disappeared from 'ls'.

Also.. when I unzip a file.. it seems that the temp files used by unzip still lingers... cause initially I have X free space... and the file i unzipped out is Y size.. but the amount of free space left is less than X-Y.. something else seems to be taking up my space

I tried apt-get clean, autoclean, autoremove, localpurge, orphan packages.. but none of this seems to work. what shld I do?

---

### Post by Vadi on 2008-08-27
Tried checking in root's trash? alt+f2, "gksudo nautilus", and click on Trash in the left sidebar.

---

### Post by Zhane on 2008-08-27
nothing there =(

---

### Post by Vadi on 2008-08-27
Temp files are stored in /tmp which are cleared when you log out / shut down, I think.

Anyway unless you're really running out of space or missing gb's of space, I wouldn't worry about the small details - linux seems to take care of it's memory very well.

---

### Post by Zhane on 2008-08-27
but the file that ive deleted still occupies a space in the system... this is part of ubuntu's management?

---

### Post by Vadi on 2008-08-28
Maybe it went to trash?

---

### Post by Zhane on 2008-08-29
bleah

now i go to gksudo nautilus
click on trash, i get an error
saying the operation cannot be supported.

I checked my trash, but there's nothing inside
i'm not sure about the root's trash..cause I cant find it now

---

### Post by Zhane on 2008-08-29
i deleted my files using "rm -rf xxx" when im in root...
now those files are still hogging to the space .. :(

I cant find /root/.Trash/
but I have /root/.local/share/Trash/ << my files aint inside here

---

### Post by Vadi on 2008-08-29
When you use rm -rf, files don't go to trash. They get permanently deleted. It's only when you delete with nautilus that they do

---

