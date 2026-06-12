---
title: "Trouble mounting floppy"
date: 2005-01-19
forum: Hardware &amp; Laptops
---

### Post by David Haas on 2005-01-19
I've formatted the floppy with the GUI as type ext2, but not mounted it successfully. I've tried various shell commands as root, such as "mount -t ext2 /dev/fd0 /media floppy." What command is correct?

---

### Post by David Haas on 2005-02-14
:-) Problem solved. After formatting the floppy, I mounted it with the command (as root) "mount -t ext2 /dev/fd0 /media/floppy"

---

