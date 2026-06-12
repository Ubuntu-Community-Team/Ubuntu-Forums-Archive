---
title: "What handles suspend in Jaunty, and where are it's resume scripts?"
date: 2009-08-18
forum: Hardware
---

### Post by lumix on 2009-08-18
It appears not to be /etc/acpi/resume.d as I've added a (working) script there that doesn't run at wake-up time.  So what scripts do run when Jaunty wakes up?

---

### Post by lumix on 2009-08-19
C'mon, this should be an easy one for the experts...

---

### Post by lumix on 2009-08-19
Anyone?  ...Bueller?

---

### Post by amd-64 on 2009-08-19
Depends on what you have installed. There is pm-tools under /etc/pm, unless you have installed uswsusp or tuxonice. Check for details in /etc/pm/config.d

---

### Post by lumix on 2009-08-19
As a matter of fact it is pm-utils

For those looking (again, Jaunty users--I think they switched over from acpi a release or two ago), you can either add a function like I did to /etc/pm/sleep.d/99laptop-mode, or create a new script.  Yes I know it's the "sleep.d" directory, but each script is executed on both cycles with either "suspend" or "resume" passed into it as the first (and only?) argument.  Thus most scripts will have a "case" statement.

---

