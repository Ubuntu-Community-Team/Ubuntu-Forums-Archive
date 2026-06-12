---
title: "Formatting External Hard Drives"
date: 2009-02-01
forum: Hardware
---

### Post by wangsuda on 2009-02-01
I wish to format an external hard drive. The hard drive is a Western Digital Caviar WD3000JB 300 GB. I have Ubuntu 8.10 (WUBI) installed along side Windows XP SP3 on an Acer Aspire 3680. So how do I use Ubuntu to format the hard drive? Thanks!

---

### Post by dkev on 2009-02-01
Download gparted and use that. Piece of cake.
*sudo apt-get install gparted*

---

### Post by wangsuda on 2009-02-01
> **dkev said:**
> Download gparted and use that. Piece of cake.
*sudo apt-get install gparted*

OK, got it. Now, if I open gparted, call up the drive, unmount it, then it allows me to reformat. What is the recommended format? ext2, ext3 or linux-swap?

---

### Post by dkev on 2009-02-02
> **wangsuda said:**
> OK, got it. Now, if I open gparted, call up the drive, unmount it, then it allows me to reformat. What is the recommended format? ext2, ext3 or linux-swap?

ext2

---

