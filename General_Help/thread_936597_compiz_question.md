---
title: "compiz question"
date: 2008-10-03
forum: General Help
---

### Post by Vertoxic on 2008-10-03
i just installed compiz setting manager... and when i go in to it under  "general options" i cant click 4 desktops its stuck on 1 why is that? i have my visual effect set to "extras" and my video drivers enabled!

---

### Post by Vertoxic on 2008-10-03
bump* anyone know why i have my desktop cube on and all... just cant use the cube do i need to download something else?

---

### Post by binbash on 2008-10-03
Try these commands (BOTH)

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

---

### Post by Vertoxic on 2008-10-03
> **binbash said:**
> Try these commands (BOTH)

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1
that didnt work :(

---

### Post by binbash on 2008-10-03
Are you sure you did this : 

System > Preferences > Appearance > CompizConfig Settings Manager

Go to General Options > Desktop Size > Make Horizontal Virtual Size 4 and others 1?


Then Ctrl + Alt  +Move the mouse

---

### Post by overdrank on 2008-10-03
Moved :)

---

### Post by Vertoxic on 2008-10-03
> **binbash said:**
> Are you sure you did this : 

System > Preferences > Appearance > CompizConfig Settings Manager

Go to General Options > Desktop Size > Make Horizontal Virtual Size 4 and others 1?


Then Ctrl + Alt  +Move the mouse
yes i did all that still no worky :(

---

### Post by overdrank on 2008-10-03
> **Vertoxic said:**
> yes i did all that still no worky :(

Hi and on the main page of CCSM (advance desktop effects) do you have desktop cube and rotate cube checked?

---

