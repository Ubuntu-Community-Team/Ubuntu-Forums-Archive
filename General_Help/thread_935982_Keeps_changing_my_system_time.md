---
title: "Keeps changing my system time"
date: 2008-10-02
forum: General Help
---

### Post by killerclick on 2008-10-02
I want to make the system time in BIOS off limits to Ubuntu. It must never change it, ever. Right now, when I boot to Windows, my time is pushed back two hours (difference between GMT and my local time).

Does anyone know how to fix this?

---

### Post by _sAm_ on 2008-10-02
In a terminal:
sudo nano /etc/default/rcS

Change UTC=no to UTC=yes 
Save and leave and the problem is gone:-)


More info here if you want: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by killerclick on 2008-10-02
Thanks for your reply but UTC is already set to 'yes'. Should I set it to 'no' perhaps?

> **_sAm_ said:**
> In a terminal:
sudo nano /etc/default/rcS

Change UTC=no to UTC=yes 
Save and leave and the problem is gone:-)


More info here if you want: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

### Post by Calmatory on 2008-10-02
I'd try setting the timezone to something which is GMT+0 and then set the correct time. If I am not mistaken, this should remove the problem.

---

