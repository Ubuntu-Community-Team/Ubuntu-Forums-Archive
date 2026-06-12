---
title: "Ubuntu or BIOS reading my HD wrong? simple question"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by jmbenson89 on 2008-01-15
When I go into the BIOS, it tells me my HD is ~10,000 MB (10 GB), but when I boot into Ubuntu, it tells me the drive is ~20 GB.  I don't know the actual size since I recently acquired this old business machine.  Is there a way to definitively find out?

Thanks.

---

### Post by chewearn on 2008-01-15
Ubuntu is probably right, since the BIOS could be so old, it doesn't read the HD properly.  But to definitely find out, you can read the HD label itself.

---

### Post by DerHesse on 2008-01-15
$ df -h

will show you the total space and space available.

If you tried to install Windows, it would probaly trust in what the bios says, and would let you use 10GB, only.

---

### Post by Thanoulis on 2008-01-15
Usually the HD manufacturer has a label on it saying what capacity it has...try to look at your disk.
But i believe that Ubuntu is right...it probably is 20GB.

---

### Post by jmbenson89 on 2008-01-15
Using the $ df -h  command said the same 20.5 GB in Ubuntu.  Just for fun, I put the HDD in my XP machine as a secondary drive and it also came up as ~20 GB, so maybe I just need to update my BIOS.

---

