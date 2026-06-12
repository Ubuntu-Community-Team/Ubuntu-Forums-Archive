---
title: "hp laser1020 not working"
date: 2009-05-11
forum: Hardware
---

### Post by Heeter on 2009-05-11
Hi all,

I just moved over from Opensuse to Ubuntu 9.04. The existing HP1020 laser was connected to the opensuse and was working fine.

I cannot get it to print from the new ubuntu os. I plugged it in, and ubuntu recognized and downloaded a hp plugin. I rebooted the workstation. It spools up during reboot but won't print when I want to print.


Any help will be greatly appreciated.


Thanks

Heeter

---

### Post by drs305 on 2009-05-11
Welcome to ubuntu and the ubuntu forums.

Take a look at this thread. The posts starting around #26 deal mostly with th e 1020. Read through them all before doing any of them as some had mixed results. If you still have problems report back with what failed to work for you, or continue that thread.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7167875#26]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7167875")

---

### Post by Lampi on 2009-05-11
i have the same printer running fine using debian/lenny and ubuntu.

Have a look at /usr/share/foo2zjs/firmware - I bet you are only missing the firmware file for HPLJ 1020 - it's called **sihp1020.dl**

You can download it from [www.linuxprinting.org]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020")

---

### Post by Heeter on 2009-05-11
Thanks for your help guys, a lot.


I have got it working now.


Thanks again


Heeter

---

