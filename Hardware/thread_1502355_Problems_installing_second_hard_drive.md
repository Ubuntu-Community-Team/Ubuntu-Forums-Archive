---
title: "Problems installing second hard drive"
date: 2010-06-05
forum: Hardware
---

### Post by klaustus on 2010-06-05
I've just tried to install a second HDD in my ubuntu desktop following this how to [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) and whilst now the drive appears to be mounted and there is an icon on the desktop, I cannot move any files to it nor create folders.

There is one folder already in the folder labelled as lost+found which I also cannot edit.

Any help on what I could do to actually be able to use this new drive would be really useful!

Thanks,

Nick

---

### Post by b0b138 on 2010-06-05
Linux doen't give user access to the drive by default. Best thing to do is run ```
gksudo nautilus
``` then navigate to the new drive and make a new folder and change the permessions of that folder to you.

---

### Post by klaustus on 2010-06-06
Fantastic - that seems to have sorted it!

Thanks a lot for your help.

---

