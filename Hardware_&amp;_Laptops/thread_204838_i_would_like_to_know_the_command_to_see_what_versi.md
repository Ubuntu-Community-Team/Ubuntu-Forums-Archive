---
title: "i would like to know the command to see what version of ubuntu i have"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by Choness on 2006-06-27
what is the command to see what version of ubuntu you have

---

### Post by Zimmer on 2006-06-27
I don't know about a 'command' but if you go to System>Help it will show you...
Did you specifically need a Terminal command for such info? for a script, maybe?

---

### Post by CrunchyDoodle on 2006-06-27
[QUOTE=Choness]what is the command to see what version of ubuntu you have[/QUOTE]


Try: uname --help
Or: uname -a

Bye.     :cool:

---

### Post by PerfMonk on 2006-06-28
You may try  :  **cat /proc/version**
in a  shell.

**uname** gives you your kernel version, but **/proc/version** add the version of the compiler and the distro name and version.

Regards,
      BT

---

