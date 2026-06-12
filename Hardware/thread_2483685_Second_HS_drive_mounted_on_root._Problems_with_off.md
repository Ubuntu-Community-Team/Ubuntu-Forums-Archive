---
title: "Second HS drive mounted on root. Problems with office suite"
date: 2023-02-06
forum: Hardware
---

### Post by pautorras on 2023-02-06
Hi,

With a Lenovo Laptop, with two ssd hard drives, I've a problem to open documents like .doc or .xls with LibreOffice or similar software suites.
The second drive was not mounted automatically by Ubuntu, so I follow these steps to be able to access file system on laptop boot.

[https://askubuntu.com/questions/769974/how-to-automatically-mount-2nd-internal-hard-drive](https://askubuntu.com/questions/769974/how-to-automatically-mount-2nd-internal-hard-drive)

In second drive I've some Virtual Machines, that vmware open without any problem.

If I try to open a .doc or .xls from this second drive on LibreOffice it says that file not exists. If I try to open the document located on second drive by Libreoffice, It does not access to same files I see in file browser.
See attached screenshots.

What is wrong?

---

### Post by TheFu on 2023-02-06
Is libreoffice on your system a snap package?

```
snap list
```

Snap packages run inside a constrained environment. They don't have access outside your HOME directory by default and cannot access anywhere else without specific permissions of the snap packaging team.  There's no local override for areas the snap programmers didn't hard code.

So, you might want to not use a snap package version. Just be more careful about which versions of packages you install. There are a few programs that are only shipped as snap packages anymore, but that number is really small. Most are available as snaps, flatpaks, appimages, through a trusted PPA or from a .deb file download.  It is your choice which of those best meets your needs. They each have good and bad aspects.

---

### Post by pautorras on 2023-02-07
> **TheFu said:**
> Is libreoffice on your system a snap package?

```
snap list
```

Snap packages run inside a constrained environment. They don't have access outside your HOME directory by default and cannot access anywhere else without specific permissions of the snap packaging team.  There's no local override for areas the snap programmers didn't hard code.

So, you might want to not use a snap package version. Just be more careful about which versions of packages you install. There are a few programs that are only shipped as snap packages anymore, but that number is really small. Most are available as snaps, flatpaks, appimages, through a trusted PPA or from a .deb file download.  It is your choice which of those best meets your needs. They each have good and bad aspects.


Thanks, now I know something else about Linux. Thanks!!

---

### Post by TheFu on 2023-02-07
> **pautorras said:**
> Thanks, now I know something else about Linux. Thanks!!

Actually, snaps are something you'll usually only see in Ubuntu flavors, not across Linux distros.  Many (distros and people) go out of their way to avoid Snap packages.

---

