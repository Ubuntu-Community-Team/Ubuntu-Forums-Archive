---
title: "hard drive not detected after upgrade to gutsy"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by lennartack on 2007-09-29
Hi,

I upgraded to gutsy today, and after rebooting one of my two drives wasn't detected anymore(/dev/sdb and /dev/sdbx don't exist).

One of the two disk is first master(the disk that isn't detected), and the other disk is third master(the disk where ubuntu is installed on). Grub calls the third master hd0 and ubuntu /dev/sda, though before the upgrade ubuntu called it /dev/sdb. 

So, what's happened and how can I make ubuntu detect my hd?

Thanks,

Lennart

---

### Post by lennartack on 2007-09-29
I hoped that a fresh install of gutsy would help maybe, but also in the live cd, only /dev/sda exists :(. Is it a bug in gutsy or is my hd broken? The bios just recognizes it...

---

### Post by lennartack on 2007-09-30
I fixed the problem by changing a jumper on the hard disk :)

---

