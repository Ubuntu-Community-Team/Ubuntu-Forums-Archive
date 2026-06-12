---
title: "(How to/Best Tutorial) I need help with Ubuntu manual partition"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by catiusca on 2008-01-15
I ahve an 500GB hard-drive and I would like to use it for Ubuntu only. What is the best manual partition for my 500GB hard-drive (with 3 partitions plus if needed swap /, /home, etc)? I don't know what is the exact config one. I need brief/detail explanation. This being the only drive on the system. Thanks so much.

---

### Post by c0met on 2008-01-15
I'd set aside the following...
[LIST]
[*]/ (28 GB)
[*]/SWAP (2 GB)
[*]/home (70 GB)
[*]2 x 200 GB patitions
[/LIST]
How does that sound?

---

### Post by catiusca on 2008-01-15
> **c0met said:**
> I'd set aside the following...
[LIST]
[*]/ (28 GB)
[*]/SWAP (2 GB)
[*]/home (70 GB)
[*]2 x 200 GB patitions
[/LIST]
How does that sound?


Meaning as:

[*]/ (28 GB)
[*]/SWAP (2 GB)
[*]/home (70 GB)
[*]2 x 200 GB patitions ---- hda1 X amount of GB and hda2 X amount of GB ?

Btw, which filesystem need to be? ext3 all partitions or which and whic does not?

---

### Post by c0met on 2008-01-15
The link below has some good information regarding installing Linux systems

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by c0met on 2008-01-15
Hi again,

I'm pretty new to Ubuntu, but how I understand things at the moment are that...

/ must be ext2 or ext3 (I use ext3)
/swap is formatted as SWAP
/home needs to be ext2 or ext3 too (again I use ext3)

[COLOR="DarkRed"]Note: If you choose to have FAT32 partitions, the maximum filesize they can handle is 4 GB which means you could not backup a 4.7 GB DVD if you used FAT32.[/COLOR]

There is some good information about setting up your system on the thread below. If you have a look at that, I think it will give you the necessary information.

[http://ubuntuforums.org/showthread.php?t=668029]("http://ubuntuforums.org/showthread.php?t=668029")

---

### Post by catiusca on 2008-01-15
> **c0met said:**
> Hi again,

I'm pretty new to Ubuntu, but how I understand things at the moment are that...

/ must be ext2 or ext3 (I use ext3)
/swap is formatted as SWAP
/home needs to be ext2 or ext3 too (again I use ext3)

[COLOR="DarkRed"]Note: If you choose to have FAT32 partitions, the maximum filesize they can handle is 4 GB which means you could not backup a 4.7 GB DVD if you used FAT32.[/COLOR]

There is some good information about setting up your system on the thread below. If you have a look at that, I think it will give you the necessary information.

[http://ubuntuforums.org/showthread.php?t=668029]("http://ubuntuforums.org/showthread.php?t=668029")

Thank you for your info . From what I see is it seems that ext3 is the favorite.

I heared people using NTFS with ubuntu instalation as  Unbuntu standalone. Not sure how much of a recommandation could that be.

---

