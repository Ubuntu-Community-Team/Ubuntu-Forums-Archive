---
title: "lilo equivaltent commnad for Grub"
date: 2008-09-05
forum: General Help
---

### Post by pcrew on 2008-09-05
back in the days we could use the following command in lilo to boot alternative kernel or os at next reboot.. is there any equivalent command for Grub?

lilo -R "title"

would boot the kerel or os defined under scetion "title" of the lilo.conf file

what is the equivalent command of this for Grub..

basically i am trying to script this functionality for my automated testing where i boot into Ubuntu and run my app tests and then i have to boot into windows to run the same tests for my windows version of the app..


currently i need manual intervention during reboot to select the windows boot entry from the grub boot loader menu..

i would like to script it to avoid the manual intervention.. any assistance is highly appreciated

---

### Post by cb951303 on 2008-09-05
in grub you don't need it because you can change the kernel on-the-fly at boot menu. just press "e" at grub menu to edit menu entries. then press "b" to boot the new entry

cheers:popcorn:

---

### Post by pcrew on 2008-09-05
cb951303
thanks for your quick help but that still requires manual intervention which is not what i am looking for.. i can do that by just selceting my boot entry from the menu .. i do not need to edit the kernel parameters and than ask grub to boot.

---

### Post by unutbu on 2008-09-05
Put "default saved" in your menu.lst instead of "default 0". Then you can use```

/usr/sbin/grub-set-default NUM
```
to set the default boot stanza.

See [http://www.gnu.org/software/grub/manual/grub.html#Invoking-grub_002dset_002ddefault](http://www.gnu.org/software/grub/manual/grub.html#Invoking-grub_002dset_002ddefault)

---

### Post by cb951303 on 2008-09-05
> **pcrew said:**
> cb951303
thanks for your quick help but that still requires manual intervention which is not what i am looking for.. i can do that by just selceting my boot entry from the menu .. i do not need to edit the kernel parameters and than ask grub to boot.

sorry I completely misunderstood the original question.

---

