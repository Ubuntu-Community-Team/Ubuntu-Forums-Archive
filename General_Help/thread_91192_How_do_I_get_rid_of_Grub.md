---
title: "How do I get rid of Grub?"
date: 2005-11-16
forum: General Help
---

### Post by HIGHLIFE on 2005-11-16
Ok so I took the hdd out of my old computer that had hoary on it so that I couls use it on my new computer so now I am getting the GRUB error 21 and I can't boot into windows.  Does anyone have any idea how I get can rid of GRUB so I can just go into windows?

---

### Post by rcerreto on 2005-11-16
Boot from windows installation CD.
You'll have an option to start a "recovery console".
After providing Administrator's password it will open a command line interface.
Enter:

fixmbr
fixboot

maybe you have to enter them in different order, can't remember now. Just try, no more than two attempts needed :-)

this will reinstall windows' boot loader.

---

### Post by HIGHLIFE on 2005-11-16
Is there a defualt administrator password, I'm not sure I remmber entering an administrator password when I loaded windows?

---

### Post by Maverick911 on 2005-11-16
After starting recovery console from the Wiindows install disk you will be asked for the administrator password. If you just hit enter you should log into your windows installation. Run fixmbr to rewrite the master boot record and Windows should boot.

Regards:smile:

---

### Post by HIGHLIFE on 2005-11-16
nvm I figured it out thx for the help:o:smile: .

---

