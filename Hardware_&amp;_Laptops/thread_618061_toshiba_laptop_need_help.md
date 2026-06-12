---
title: "toshiba laptop need help"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by kle111 on 2007-11-20
I have this laptop and installed ubuntu .It is working fine but i cant activate or enable cd/dvd drive on bios .
I have tried about everything i could think of except format and reinstall 
wich i do not want to do if any-one has any idea please help 

:mad::mad:

---

### Post by ayampanggang on 2007-11-20
what types of toshiba are you using?

if it's about activating/deactivating cdrom from bios i believe it's got nothing to do with ubuntu.

if you actually meant your cdrom is not detected by ubuntu though, check if ubuntu recognize it; open terminal and type this straight away:
```

ls /dev | grep cdrom
ls /dev | grep scd

```
verify if the cdrom got detected. if they do there should be output like:
```

cdrom
scd0

```

---

### Post by kle111 on 2007-11-20
it is a toshiba satellite L30 psl33e

If i go into bios the cdrom is there but unable to select it 
On help it says f5 and f6 to move selection up down +- does the selection and enter on it change the selection to what you want .

My problem is hdd has a + next to it and i am unable to select cdrom or any other that is in the list  .

---

### Post by kle111 on 2007-11-21
doesnt seem to have any answer anywhere 
used partition tool format drive then could select cd/dvd on multiboot selection 

installed windows and linux and can boot any-one now

---

