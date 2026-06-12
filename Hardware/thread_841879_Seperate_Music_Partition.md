---
title: "Seperate Music Partition"
date: 2008-06-26
forum: Hardware
---

### Post by patrickaupperle on 2008-06-26
I just installed opneSUSE as a dualboot with Ubuntu. I want my music on an ext3 formatted partition that automagically mounts to /home/patrick/Music on both openSUSE and Ubuntu. I am pretty sure this is possible, but don't know how.

---

### Post by entropy_ on 2008-06-26
> **patrickaupperle said:**
> I just installed opneSUSE as a dualboot with Ubuntu. I want my music on an ext3 formatted partition that automagically mounts to /home/patrick/Music on both openSUSE and Ubuntu. I am pretty sure this is possible, but don't know how.

Create a partition and edit your /etc/fstab by adding a line like

```
/dev/sda4    /home/patrick/Music    ext3    defaults    0 1
```

on both installs. It should automount the music directory on every boot.

---

### Post by patrickaupperle on 2008-06-27
> **entropy_ said:**
> Create a partition and edit your /etc/fstab by adding a line like

```
/dev/sda4    /home/patrick/Music    ext3    defaults    0 1
```

on both installs. It should automount the music directory on every boot.

Thank you. As soon as I get ubuntu to boot (I found an easy way to mount it in openSUSE), I will try this.

---

