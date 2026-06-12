---
title: "kernel update problem: 2.6.10-34.3"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by epa on 2005-06-29
Yesterday I did a apt-get update && apt-get dist-upgraded and a new kernel was installed. When I later rebooted, GRUB appeared and then, when Ubuntu selected, seems to boot something but can't see anything on the screen, and fan starts working as if microprocessor was working at 100% (which is unusual at least in this computer when booting ubuntu).

I'm now running ubuntu with a kernel compiled in a debian, so I can use apt, etc. but I don't know what to do.

What can be happening? Did anybody else have this problem?

Thank you in advance

---

### Post by epa on 2005-06-29
It also happens with the kernel compiled for 386

---

### Post by nocturn on 2005-06-29
[QUOTE=epa]It also happens with the kernel compiled for 386[/QUOTE]

I haven't noticed such problems.  Maybe you should file a bugreport [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/), I'm sure it will be resolved.

---

### Post by epa on 2005-06-29
[QUOTE=nocturn]I haven't noticed such problems.  Maybe you should file a bugreport [https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/), I'm sure it will be resolved.[/QUOTE]

Thanks, done:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=12245](https://bugzilla.ubuntu.com/show_bug.cgi?id=12245)

---

### Post by ianpeters on 2005-06-29
[QUOTE=epa]Yesterday I did a apt-get update && apt-get dist-upgraded and a new kernel was installed. When I later rebooted, GRUB appeared and then, when Ubuntu selected, seems to boot something but can't see anything on the screen, and fan starts working as if microprocessor was working at 100% (which is unusual at least in this computer when booting ubuntu).

I'm now running ubuntu with a kernel compiled in a debian, so I can use apt, etc. but I don't know what to do.

What can be happening? Did anybody else have this problem?

Thank you in advance[/QUOTE]
 Haven't noticed this either. On the other hand I never use dist-upgrade, only the Update Manager. And I always turn off unofficial repositories while doing upgrades....just in case.

---

