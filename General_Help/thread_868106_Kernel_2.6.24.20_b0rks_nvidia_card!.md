---
title: "Kernel 2.6.24.20 b0rks nvidia card!"
date: 2008-07-23
forum: General Help
---

### Post by zachtib on 2008-07-23
I just updated to the latest kernel, and I can't get my nvidia card working... Anyone have the same problem

---

### Post by bp1509 on 2008-07-23
how'd you manage to do that?  2.6.24-19-generic is the latest stable for Ubuntu.

---

### Post by Jimmey on 2008-07-23
The restricted modules for that kernel have probably not been packaged yet.

---

### Post by Ebuntor on 2008-07-23
> **Jimmey said:**
> The restricted modules for that kernel have probably not been packaged yet.

Yes, they have. They're listed as updates along with the other 2.6.24.20 kernel packages.

---

### Post by Shazaam on 2008-07-23
It's from "Hardy-proposed". So it could be called "beta".:)

---

### Post by Joeb454 on 2008-07-23
Moved to General Help.

2.6.24-20 is in Hardy-proposed I assume, as I've not received it yet (and that's the only repo I don't enable). I suggest disabling that if you don't want similar things occuring in future - they're "proposed" for a reason :p

---

### Post by steveneddy on 2008-07-23
Intel Core 2 Duo with Nvidia works fine here on 64 bit Ubuntu.

I have proposed and backports enabled.

---

### Post by sdennie on 2008-07-23
How did you install the drivers initially?  If you installed them by downloading from the nvidia website, you will have to re-install them after any kernel update where the version number changes.  You can prevent that in the future with this guide: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

