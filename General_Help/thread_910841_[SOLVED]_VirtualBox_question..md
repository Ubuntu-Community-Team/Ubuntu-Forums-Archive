---
title: "[SOLVED] VirtualBox question."
date: 2008-09-04
forum: General Help
---

### Post by Newuser1111 on 2008-09-04
Is there a way to convert VHD to VDI without "vboxmanage"?
Because it requires the OSE version to use "vboxmanage".

---

### Post by bingoUV on 2008-09-05
qemu can convert between these file formats. I don't remember exactly what you have to run, but the man page should help.

```

apt-get install qemu
man qemu-img

```

---

### Post by Newuser1111 on 2008-09-05
Is this the right command?
```
qemu-img convert Win98.vhd Win98.vdi
```

Because it seems to be doing something.

---

### Post by Newuser1111 on 2008-09-05
How can I convert it from a dynamic VHD and to a dynamic VDI instead of changing to a fixed-size one?

---

### Post by gjoellee on 2008-09-05
you should get the latest version of Virtual Box (v. 2.0) it was released today

---

### Post by Newuser1111 on 2008-09-05
> **gjoellee said:**
> you should get the latest version of Virtual Box (v. 2.0) it was released todayDoes it allow to use VHDs without converting? **Edit: The changelog says it can!**
**Edit2: THANKS!!!**

---

