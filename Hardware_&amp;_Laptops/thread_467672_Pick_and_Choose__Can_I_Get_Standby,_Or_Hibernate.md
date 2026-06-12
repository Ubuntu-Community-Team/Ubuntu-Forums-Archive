---
title: "Pick and Choose:  Can I Get Standby, Or Hibernate?"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by DizzyTech on 2007-06-08
If only I could get both Suspend and Suspend-to-Disk working on my Compaq Presario V5204NR... but, no.  With the default Ubuntu settings (and one or two edits to the /etc/default/acpi-support file), I can suspend, but not hibernate.  Following instructions to get hibernate working, I install the uswsusp and hibernate packages.  Oh, yes, hibernate works excellent!

...But suspend does not.

What do I do?

---

### Post by scrooge_74 on 2007-06-08
Do you have enough space in the swap file so at suspend time the system can write to disk?

---

### Post by eentonig on 2007-06-08
He should have, or hibernation shouldn't work.

And Standny doesn't flush the RAM tp disk if I'm not wrong.

Sorry, can't help you

---

### Post by Sweet Mercury on 2007-06-08
> **DizzyTech said:**
> If only I could get both Suspend and Suspend-to-Disk working on my Compaq Presario V5204NR... but, no.  With the default Ubuntu settings (and one or two edits to the /etc/default/acpi-support file), I can suspend, but not hibernate.  Following instructions to get hibernate working, I install the uswsusp and hibernate packages.  Oh, yes, hibernate works excellent!

...But suspend does not.

What do I do?

You got your comp to suspend? How? That's the last major hurdle I'm facing with my laptop...

---

### Post by DizzyTech on 2007-06-08
I had /etc/default/acpi-support read the same as the file I attached.  However, when I installed uswsusp to get Hibernation working, standby stopped (but Hibernate worked)

---

### Post by scrooge_74 on 2007-06-08
[http://www.ubuntuforums.org/showthread.php?t=237264&highlight=suspend+hibernate+howto](http://www.ubuntuforums.org/showthread.php?t=237264&highlight=suspend+hibernate+howto)

hope this helps

---

### Post by DizzyTech on 2007-06-10
That worked!  Yipee!

I just had one problem... instead of adding "noacpi acpi=off apm=on nolapic" to my grub list, I added "noacpi apm=on nolapic," omitting the acpi=off, because it glitched out my keyboard and Touchpad.  But, thanks!

---

