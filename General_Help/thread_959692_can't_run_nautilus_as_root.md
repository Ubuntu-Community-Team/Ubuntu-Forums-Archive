---
title: "can't run nautilus as root"
date: 2008-10-26
forum: General Help
---

### Post by T2manner on 2008-10-26
i try to run it in terminal, but this is what i get
```
tyler@tyler-laptop:~$ gksudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
(nautilus:11629): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:11629): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed
tyler@tyler-laptop:~$ 

```

---

### Post by fjgaude on 2008-10-26
Seems your GLib is giving troubles... you might try rebooting using the Recovery mode in the Grub menu, and then doing a package check from the commandline.

---

### Post by T2manner on 2008-10-26
how do i do a package check from the command line?

---

### Post by LowSky on 2008-10-26
what do you need to enter naulitus as root for?

---

### Post by T2manner on 2008-10-26
so i can make a backup of my home folder by making an archive of it.

---

