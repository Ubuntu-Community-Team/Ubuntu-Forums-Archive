---
title: "Issues after upgrade 8.04 to 9.04"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by Surendra on 2009-05-23
Hi everybody,
Till y'day i am using ubuntu server 8.04 in virtual pc 2007. Today i upgrade to 9.04, After completion of the install i restarted my server, then i am getting below message.

[B]This kernel requires the following features not present on the CPU.
pae
Unable to boot  - Please use a kernel appropriate for your CPU.
[/B]

Is any idea how to resolve this.

Thanks in Advance

---

### Post by cariboo on 2009-05-23
Did you follow the correct procedure to update?

[list]
[*] disable ppa's and third party repositories
[*] make sure current version is fully up to date
[*] update path should be 8.04.2-->8.10-->9.04
[/list]

---

### Post by Surendra on 2009-05-23
Yes I did same procedure. First i upgrade to 8.10 and then 9.04. It was completed successfully. once i reboot the system then got above message.

---

