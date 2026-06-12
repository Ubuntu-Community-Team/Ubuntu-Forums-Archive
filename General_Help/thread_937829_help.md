---
title: "help"
date: 2008-10-04
forum: General Help
---

### Post by kuliuli on 2008-10-04
i forgot my administrators's password and now i can't install things like wine is there any way that i can find the password?

---

### Post by Nepherte on 2008-10-04
Boot into the recovery mode. You will end up with a console with the root user.

To change the password of root:
```
passwd root
```
and type in your password (you will be asked to do it twice). Note that you don't see any *** that indicate you typed a character.

To change the password of a given user:
```
passwd USERNAME
```
replace USERNAME with a real user.

Afterwards you can boot normally.

---

### Post by kuliuli on 2008-10-04
i don't understand what is recovery mode

---

### Post by porchrat on 2008-10-04
When your computer first boots (I mean before Ubuntu even starts to load) up there are two possibilities:

A) If you are dual-booting you will see a simple-looking menu (called GRUB) that has a few options in it.  One of those options will be Ubuntu (some or other version)...and another option will be "Ubuntu Recovery mode".  In this case select "ubuntu recovery mode" to boot in the Ubuntu equivalent of the Windows "Safe Mode".

B) If you are not dual booting, then while the machine is booting up you will see a message on the screen saying something along the lines of "press ESC to see the GRUB boot menu".  At this point press ESC and you will see the menu mentioned in (A) above.  Then select "Ubuntu Recovery Mode".

As I said before Ubuntu Recovery Mode is basically like a Windows Safe Mode where Ubuntu will load with very few bells and whistles to minimise the possibility of a problem occurring.  From this mode you can change the root password.

---

