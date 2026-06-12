---
title: "sudo nautilus broken"
date: 2008-08-13
forum: General Help
---

### Post by weweboom on 2008-08-13
when I try to open nautilus as root I get 

seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault

help would be appreciated, thanks

---

### Post by p_quarles on 2008-08-13
What happens when you use the proper method for doing this?:
```
gksu nautilus
```

---

### Post by weweboom on 2008-08-13
nothing happens, it doesn't load or anything

---

### Post by p_quarles on 2008-08-13
I'd suggest taking a look at the Nautilus and Seahorse settings in the /root directory of the filesystem (you should be able to read them just fine without root privileges). See if anything is amiss.

If you don't see anything, I would say to try moving those settings to backup files and starting with "fresh" configurations for the root user. If this is the only option, it will be easy for me or someone else to guide you through the CLI steps needed to do this.

---

### Post by mc4man on 2008-08-13
Do you happen to have 'unmountable media' like a blank cd or dvd in drive? (or somehow elsewhere

 When you run gksu(do) nautilus the system mounts any unmounted removable media under root and if it can't then you segfault or nothing happens.

---

### Post by prshah on 2008-08-13
> **weweboom said:**
> when I try to open nautilus as root I get 
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault


First of all, using nautilus in root mode is a _bad_ idea.

For your specific problem, make sure that there is no blank CD/DVD in the drive before starting root mode nautilus.

EDIT: Apparently there is a workaround for root-mode nautilus with a blank CD/DVD disc in the drive: use ```
sudo dbus-launch nautilus
```

---

### Post by p_quarles on 2008-08-13
> **prshah said:**
> First of all, using nautilus in root mode is a _bad_ idea.
No it's not.

It carries a risk of breaking things if you are careless with it, yes, but it is not inherently bad.

---

### Post by prshah on 2008-08-13
> **prshah said:**
> using nautilus in root mode is a _bad_ idea.

> **p_quarles said:**
> No it's not.
It carries a risk of breaking things if you are careless with it, yes, but it is not inherently bad.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/238668](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/238668)

The comments are interesting.

---

