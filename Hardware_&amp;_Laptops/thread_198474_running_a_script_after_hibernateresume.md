---
title: "running a script after hibernate/resume"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by kreso on 2006-06-17
I need to run a script each time my laptop resumes from hibernate and displays the locked screen, how can I set that up?

---

### Post by kreso on 2006-06-17
i found something in /etc/acpi/resume.d, put my script in that folder, but it didn't seem to've got executed after resume? :confused:

---

### Post by afsahabi on 2008-01-21
make sure the script owner is root/root and chmod them to 755.

---

