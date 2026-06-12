---
title: "Corrupted disklabel"
date: 2008-12-23
forum: Hardware
---

### Post by andrewboktor on 2008-12-23
I have a 40 GB Harddisk, now the problem seems is that the place where the disklabel is stored seems to be corrupted thus, whenever i create a new disklabel and a partition table those things seem to get lost after removing and reconnecting my device. Any ideas how to solve that?
(also my diagnosis might be wrong, please let me know if you think about any other possible causes)
Please let me know if you need any additional information, i will try to provide them ASAP.

Thank You in advance

---

### Post by logos34 on 2008-12-23
so you're using tune2fs or e2label?

---

### Post by andrewboktor on 2008-12-24
> **logos34 said:**
> so you're using tune2fs or e2label?
I am not talking about the partition label, i am talking about the disklabel, like msdos disklabel, like wt's done by the command "parted mklabel msdos".

---

### Post by logos34 on 2008-12-24
oh, I see, I'm more familiar with it on the Gparted gui (Device>Set disklabel)

---

### Post by logos34 on 2008-12-24
when you run

sudo parted /dev/sd?

> print

what exact error message do you?  'Unable to open', 'unrecognized disk label', what?

what version are you using?

could be [a bug]("http://www.gnu.org/software/parted/bugs.shtml")

---

