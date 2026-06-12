---
title: "auto mount"
date: 2009-05-29
forum: Hardware
---

### Post by jj3502 on 2009-05-29
i dual boot with win xp and its on a different hdd how do i auto mount it on start up and without entering a password if possible

---

### Post by ParanoidMetroid on 2009-05-29
In a terminal, type
$ sudo aptitude install pysdm
$ gksudo pysdm

Hopefully this helps.  I found this information here: [http://sathyasays.com/2008/10/08/how-to-automount-hard-drive-partitions-everytime-you-login-in-linux/](http://sathyasays.com/2008/10/08/how-to-automount-hard-drive-partitions-everytime-you-login-in-linux/).

---

