---
title: "Does anybody know how to stop suspend/hibernate when you close the lid?"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by bnutting on 2005-05-27
I have a Dell Inspiron 5000 laptop and Hoary runs great on it. The problem is though that when I close my lid the system goes to suspend/hibernate. I would like it to just blank the screen does anybody know how/where to change this?

Thanks

---

### Post by dave9191 on 2005-05-27
Blank the screen is the default behaviour for closing the lid. The script executed when you close the lid is /etc/acpi/lid.sh. You can edit that to do whatever you want when you close the lid. 

Dave

---

### Post by bnutting on 2005-05-27
Just a tid bit, I have acpi=off apm=on as kernel parameters because of acpi issues. Will this still apply? I'm not sure I have a lid.sh script but I will check.

Thanks for the quick reply.

---

### Post by dave9191 on 2005-05-28
Ahh, Im not sure. Maybe thats why your screen isnt blanking when you close the lid. Give it a go, but google apm and see where they keep their configuration stuff. 

Dave

---

### Post by TopPretender on 2005-10-10
[QUOTE=bnutting]Just a tid bit, I have acpi=off apm=on as kernel parameters because of acpi issues. Will this still apply? I'm not sure I have a lid.sh script but I will check.

Thanks for the quick reply.[/QUOTE]


where can i change these values????

---

