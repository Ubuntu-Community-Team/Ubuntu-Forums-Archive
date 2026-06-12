---
title: "AMD64 on ARM64"
date: 2024-11-19
forum: Hardware
---

### Post by uberthoth on 2024-11-19
I have a Grace Hopper GH-200 (which is arm64) upon which I enabled qemu emulation.  At which point it now throws these errors when updating:

```
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jammy/main/binary-amd64/Packages  404  Not Found [IP: 185.125.190.39 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jammy-updates/main/binary-amd64/Packages  404  Not Found [IP: 185.125.190.39 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jammy-backports/main/binary-amd64/Packages  404  Not Found [IP: 185.125.190.39 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jammy-security/main/binary-amd64/Packages  404  Not Found [IP: 185.125.190.39 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

And, indeed, those URLs do not exist, as amd64 is not among the architecture provided by [ports.ubuntu.com]([http://ports.ubuntu.com/ubuntu-ports/dists/jammy-security/main/](http://ports.ubuntu.com/ubuntu-ports/dists/jammy-security/main/))

My sources.list:

```
grep -v '^#' sources.list|grep -v '^$'deb http://ports.ubuntu.com/ubuntu-ports jammy main restricted
deb http://ports.ubuntu.com/ubuntu-ports jammy-updates main restricted
deb http://ports.ubuntu.com/ubuntu-ports jammy universe
deb http://ports.ubuntu.com/ubuntu-ports jammy-updates universe
deb http://ports.ubuntu.com/ubuntu-ports jammy multiverse
deb http://ports.ubuntu.com/ubuntu-ports jammy-updates multiverse
deb http://ports.ubuntu.com/ubuntu-ports jammy-backports main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports jammy-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports jammy-security universe
deb http://ports.ubuntu.com/ubuntu-ports jammy-security multiverse

```

How do I fix this?

---

### Post by guiverc on 2024-11-19
*amd64* is NOT a port, and packages are not found at [http://ports.ubuntu.com/](http://ports.ubuntu.com/) but instead at [http://archive.ubuntu.com/](http://archive.ubuntu.com/)

Not all *architectures* are found at the same site; *main/primary* architectures and *ports* are at different URLs as package versions CAN VARY between them for the same release (*its rare, but it can and does happen*).

---

### Post by uberthoth on 2024-11-19
I get that, but again all I did was enable qemu, I did not alter my sources.list.   What am I supposed to do to fix it?

---

### Post by outofcheese on 2024-11-19
Did you look at your sources list directory? If you went for amd64 emulation maybe something tried to add amd64 sources and blundered. You'd fix it by putting in the proper sources in place of the "ports" ones that also contain amd64 (since like guiverc pointed out those do not exist).

---

### Post by uberthoth on 2024-11-19
that is what I'm saying, I cannot find any sources that list amd64 anywhere in that directory:

grep -ir amd64 /etc/apt/*
/etc/apt/apt.conf.d/50unattended-upgrades:    // The following matches packages like xen-system-amd64, xen-utils-4.1,

---

### Post by deadflowr on 2024-11-19
Check your architectures
```
dpkg --print-architecture
dpkg --print-foreign-architectures
```

Remove foriegn arch with

```
sudo dpkg --remove-architecture amd64
```

Alternatively you can also force the source file to only look for arm64 by adding it to each entry like

```
deb **[arch=arm64]** http://ports.ubuntu.com/ubuntu-ports jammy-updates main restricted
```

But usually easier to just remove the supported arch in dpkg.

---

### Post by uberthoth on 2024-11-19
that was it, thank you for the succinct explanation @deadflowr

---

