---
title: "Aspire-XC-603G Random freeze x64"
date: 2014-06-09
forum: Hardware
---

### Post by xkainx2 on 2014-06-09
Ubuntu 14.04 LTS

ok i think i nailed this down to Ubuntu not liking a logitech cam of mine and unplugged it but to think a bad driver could crash a kernel is kind of messed up. Is this problem only x64 or does this simply effect all Gen 7 Machines? Do they still use pae kernels in x32?

---

### Post by mörgæs on 2014-06-10
Yes, all standard 32 bit kernels in 14.04 require PAE.

---

### Post by xkainx2 on 2014-06-11
sweet. I have allways wondered why push the x64 then?

---

### Post by xkainx2 on 2014-06-12
32bit cd sadly will not boot in UEFI and sadly my board does not support Legacy / CMOS mode. Not sure what to do at this point because the slightest thing I do that Ubuntu doesn't like, it freezes rock solid before it even has time to write an error log.

---

### Post by mörgæs on 2014-06-12
You could begin with posting the exact steps you took trying to install and the results.

---

