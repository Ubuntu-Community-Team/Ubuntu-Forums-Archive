---
title: "Reducing Ubuntu partition, expanding XP"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by AcerAspirant on 2009-10-13
I need to increase the size of my Windows partition, unfortunately at the expense of Ubuntu.  My questions are:

1. If I use gparted to make Ubuntu smaller, would I also be able to use it to expand XP's size?  Would there be any complications involved in that?

2. I had a spare partition once that was supposed to be shared between the two OS, but neither seem to be able to recognize/access it.  How can I change that?

---

### Post by mechro on 2009-10-13
> **AcerAspirant said:**
> I need to increase the size of my Windows partition, unfortunately at the expense of Ubuntu.  My questions are:

1. If I use gparted to make Ubuntu smaller, would I also be able to use it to expand XP's size?  Would there be any complications involved in that?



Gparted can do what what you require usually without a hitch.

Plan for "complications" and problems by backing up your data in advance.

Also, would you know what to do if your system didn't boot after resizing the partitions?

---

### Post by mechro on 2009-10-13
> **AcerAspirant said:**
> 

2. I had a spare partition once that was supposed to be shared between the two OS, but neither seem to be able to recognize/access it.  How can I change that?

It depends what you mean by "spare". If it's unallocated space then there is nothing to recognize/access.

---

### Post by earthpigg on 2009-10-13
use ubuntu tools (gparted) to decrease the size of the ubuntu partition.

use windows tools to increase the size of the windows partition.

use windows tools to create a shared partition (i recommend fat32.).

in general:

ubuntu works well with stuff created by other operating systems.

by intentional (mis)design, windows does not work well with stuff created by other operating systems.

---

### Post by AcerAspirant on 2009-10-13
What Windows tool are you talking about?

---

### Post by Mark Phelps on 2009-10-13
Typical (commercial) Windows tools include Partition Magic, Acronis Disk Director, Paragon Partition Manager.

You can google for and download EASUS Partition Master for free.  It's the "home" version of their commercial product.

---

