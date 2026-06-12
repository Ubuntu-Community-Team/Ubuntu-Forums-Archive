---
title: "tryed to install windows but now cant get onto ubuntu"
date: 2008-09-01
forum: General Help
---

### Post by joe9110 on 2008-09-01
hi im really angry with myself because i  tryed to install windows for one reason (to play pc games) but now when i start my pc it has a black screen with text saying 
'BOOTMGR MISSING PRESS CTRL-ALT-DEL TO RESTART'
My hard drive is partioned in to two with ubuntu 8.04 on the biggest part of it and trying to put xp on the smaller part.
Im angry because ubuntu was working a treat untill i discovered i cant play my games.

is there anyway to change the part of the hard dive to boot to ?

thanks in advance

---

### Post by ken_do_san on 2008-09-01
Try a google search for repairing a boken MBR or try this link

[http://www.uneraser.com/missing-corrupted-system-files.htm](http://www.uneraser.com/missing-corrupted-system-files.htm)

:)

Cheers

---

### Post by WRDN on 2008-09-01
To boot directly into Windows, boot from the Windows installation disk (if you have it) and:

- For Windows XP, press 'r' to enter recovery mode, then enter:

```
fixmbr
```

- For Windows Vista, boot from the DVD, open the console, and type:

```
bootrec /fixboot
bootrec /fixmbr
```

Alternatively, you can [restore GRUB from the Ubuntu LiveCD]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by natirips on 2008-09-01
You'll need to reinstall GRUB (Boot loader - the program which loads operating system(s)). Try [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) .

---

### Post by Sef on 2008-09-01
> You'll need to reinstall GRUB (Boot loader - the program which loads operating system(s)). Try [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) .

+1.  Windows overwrites grub, and Windows only recognizes other Windows.

---

### Post by Nepherte on 2008-09-01
This page covers it all: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

