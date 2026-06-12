---
title: "[SOLVED] Virtual Box Modules problem"
date: 2008-08-29
forum: General Help
---

### Post by MDSmith2 on 2008-08-29
The following packages have unmet dependencies:
  virtualbox-ose-modules-2.6.24-20-generic: Depends: linux-image-2.6.24-20-generic but it is not installable but virtual box won't run without it!!!

---

### Post by Oldsoldier2003 on 2008-08-29
Your best bet is to just download and install the Puel version of Virtualbox from their website. It supports recompiling of the kernel modules so you dont have to wait for the repos to catch up.

---

### Post by knattlhuber on 2008-08-30
> **MDSmith2 said:**
> The following packages have unmet dependencies:
  virtualbox-ose-modules-2.6.24-20-generic: Depends: linux-image-2.6.24-20-generic but it is not installable but virtual box won't run without it!!!

When you run

```
uname -a
```

your kernel version is probably 2.6.24-19, right?

If that's the case, then install the 'virtualbox-ose-modules-2.6.24-19-generic' package only, even though Synaptic suggests to install the whole metapackage.

After that, add your username to the 'vboxusers' group:

```
sudo useradd -G vboxusers yourusername
```

That should do it.

---

### Post by MDSmith2 on 2008-08-31
I tried that, but it said that the package was not installable.
just nevermind it, I just got the binary off the Sun site.
thank!

---

