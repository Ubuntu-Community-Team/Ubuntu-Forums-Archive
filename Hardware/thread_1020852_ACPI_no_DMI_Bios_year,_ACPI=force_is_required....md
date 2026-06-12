---
title: "ACPI: no DMI Bios year, ACPI=force is required..."
date: 2008-12-24
forum: Hardware
---

### Post by cgaudio on 2008-12-24
...to enable ACPI.
Then I get a kernel panic message.

I get this attempting to boot (without any change...) from Intrepid live CD. Laptop is Toshiba Satellite 2505CDS.

I want to install Ubuntu, but am hesitant because I get this message. 

Will Ubuntu run if I just go ahead and install it? If not, how can I eliminate this error so I can run/install Intrepid?

You are dealing with a stone beginner here, so feed me pablum, not de fois gras.

Thanks!
-Chuck

---

### Post by Partyboi2 on 2008-12-25
Looking at the specs for the Toshiba Satellite 2505CDS you might be better off trying another lighter linux distro like [[COLOR=Blue]dsl (darn small linux)[/COLOR]]("http://damnsmalllinux.org/")

---

### Post by cgaudio on 2008-12-26
I am seeing other fixes on Google, but adding acpi=force to the command line gets me the same error message, either on install or run from the CD.

Thanks, I may try DSL later.
-Chuck

---

### Post by T-Train on 2009-01-07
I am trying to help someone install 8.10 as well and they are receiving the same error.  They tried F6, F6 and used the acpi=force but still no luck.  I am trying to help them remotely, I have never seen this issue.

---

### Post by Harii on 2009-01-07
I think its just a reminder to set the acpi=force in grub
[http://ubuntuforums.org/showthread.php?p=2595626]("http://ubuntuforums.org/showthread.php?p=2595626")

i use acpi=force and all is well.
without it my laptop doesn't shut down.

---

