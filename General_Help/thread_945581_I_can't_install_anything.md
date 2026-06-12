---
title: "I can't install anything"
date: 2008-10-12
forum: General Help
---

### Post by davideotape on 2008-10-12
Whenever I try to install anything I get this error message:

> david@david-desktop:~$ apt-get install checkgmail
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Does anyone have any idea what is going wrong?

---

### Post by nlinecomputers on 2008-10-12
To use apt-get you have to have root (administrator) rights.

In ubuntu you do this by using sudo.

Put sudo in front of your command. You will then get a  password prompt and after that it will install this.

$ sudo apt-get install checkgmail

---

### Post by earthpigg on 2008-10-12
**sudo** apt-get install checkgmail

the sudo is essential :)

---

### Post by alzie on 2008-10-12
Try using sudo apt-get install

It will prompt you for your password then it should be smooth sailing

I hope this helps

(sudo gives temporary root permissions for an install)
<edit> gotta type faster lol

---

### Post by porchrat on 2008-10-12
> **davideotape said:**
> Whenever I try to install anything I get this error message:

Does anyone have any idea what is going wrong?

you can't use apt-get unless you run it as root.

use "sudo" in front like this:

```
sudo apt-get install checkgmail
```

---

### Post by davideotape on 2008-10-12
Thanks a lot that worked straight away.

---

