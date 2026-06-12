---
title: "What's the suspend command?"
date: 2006-03-03
forum: Hardware &amp; Laptops
---

### Post by mexlinux on 2006-03-03
Hi:
I want to schedue my laptot to suspend a specific time.
But in order to do that I need to know whats the command for suspend to memory?
Thanks,
Miguel

---

### Post by prizrak on 2006-03-03
Do a system wide search for ACPI. You should hit on the directory with all the scripts that control suspend, hibernate and whatnot. I do have to warn you tho I was never succesful running the script to make suspend/hibernate from CLI/run dialog/program. Does work with the hot key somehow, don't ask me why :)

---

### Post by mexlinux on 2006-03-03
vertainly I've been digging in /etc/acpi and got to the conclusion that the command was:
/etc/acpi/sleep.sh
But it does nothing, I guess it shold be called with ceretain parameter, but I can not figure that out...

---

### Post by ciscosurfer on 2006-12-19
> **mexlinux said:**
> vertainly I've been digging in /etc/acpi and got to the conclusion that the command was:
/etc/acpi/sleep.sh
But it does nothing, I guess it shold be called with ceretain parameter, but I can not figure that out...Get root and then issue /etc/acpi/sleepbtn.sh

---

