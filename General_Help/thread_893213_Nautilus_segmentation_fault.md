---
title: "Nautilus segmentation fault?"
date: 2008-08-18
forum: General Help
---

### Post by jasex on 2008-08-18
```
thursday@Yggdrasil:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault
thursday@Yggdrasil:~$

```

??? Why would this happen, doesn't that usually mean something wrong in the code?

---

### Post by mc4man on 2008-08-18
> Why would this happen
The most common reason would be having 'unmountable' removable media present when you ran the command. Most likely candidate would be having a blank cd or dvd disc in a drive.

---

### Post by jasex on 2008-08-18
Thanks, there's a blank cd actually... is there a way to do it without removing said CD?

---

### Post by mc4man on 2008-08-18
> is there a way to do it without removing said CD? 
As far as I know not unless the behavior is changed with an update.

You can see this behavior with a different result by inserting a usb thumb drive, unmounting it but leaving it in.

Then run gksu(do) nautilus. Nautilus will open and the usb drive will be auto mounted under root. (no write perm.

---

