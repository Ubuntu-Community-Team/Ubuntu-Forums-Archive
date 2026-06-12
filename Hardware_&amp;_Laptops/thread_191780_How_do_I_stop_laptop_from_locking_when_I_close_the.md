---
title: "How do I stop laptop from locking when I close the lid?"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by mr_ed on 2006-06-08
I never take my laptop anywhere except home and work, so I never need to lock it.  How do I prevent it from locking?

---

### Post by ltmon on 2006-06-08
There's probably a few ways, but here's one that comes to mind.

I think there is a script in the directory /etc/acpi that contains the actions that should be performed on lid close.  I can't check now (away from my laptop).

It's name "lidclose.sh" or something else obvious like that, and it contains the commands run when this acpi event occurs.

Open it (as root) and comment out the actions with a "#" on each line.  Then :
```

sudo /etc/init.d/acpid restart

```

Uncomment and restart acpi again to get back to your original state if it all goes wrong :)

L.

---

### Post by Patsoe on 2006-06-08
Another (perhaps less drastic) option is to edit the config file rather than the script itself: I think the right file is /etc/default/acpi-support - the entry that you need to change is LOCK_SCREEN.

---

### Post by ltmon on 2006-06-08
[QUOTE=Patsoe]Another (perhaps less drastic) option is to edit the config file rather than the script itself: I think the right file is /etc/default/acpi-support - the entry that you need to change is LOCK_SCREEN.[/QUOTE]

Yeah.... do what he said :-\"

---

### Post by nandasunu on 2006-06-08
An even easier way is to just change the setting in the power settings area... (I'm not at home so I can't point you exactly to it, but I did this myself the other day)

---

### Post by mr_ed on 2006-06-08
Thanks!  One of them did it.  I think it was nandasunu's... I changed the setting to "Do Nothing" (I didn't want to try that one though because I actually wanted it to turn the screen off if I did that -- and it does).

Earlier on in the week, I searched for this and edited /usr/share/acpi-support/screenblank and commented out a few commands, but it did nothing. :confused:

Turns out that that's called from /etc/acpi/lid.sh

Thanks all!  :D

---

