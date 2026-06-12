---
title: "Truecrypt is read-only, how to make it writeable?"
date: 2013-10-15
forum: Hardware
---

### Post by LDA7MFe on 2013-10-15
I have a truecrypt volume as a drive mounted in /mnt/truecrypt1

However, it's read only.

Running "sudo chmod -R 775 truecrypt1":
chmod: changing permissions of 'truecrypt1/XXX': read-only file system

When I try "sudo mount -o remound,rw '/mnt/truecrypt1':
mount: cannout remound /dev/mapper/truecrypt1 read-write, is write-protected

edit: should note, I don't have the "read-only" setting on in truecrypt.

---

