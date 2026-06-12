---
title: "[SOLVED] error on update manager"
date: 2008-11-20
forum: General Help
---

### Post by jryprt on 2008-11-20
Trying to install updates but I get this error. Sorry the wrap with code button is not working .



W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb)
  Size mismatch

---

### Post by jryprt on 2008-11-20
got it I downloaded 1 at a time & used gdeb

---

### Post by lightnin on 2008-11-20
I am getting a size mismatch error using update manager too

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb
  Size mismatch


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb
  Size mismatch


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb
  Size mismatch



```

could you please give a 'quick' how to, with the gdeb thing you did

Ta

---

### Post by jryprt on 2008-11-20
> **lightnin said:**
> I am getting a size mismatch error using update manager too

```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.7.dfsg.1-0ubuntu5.1_all.deb
  Size mismatch


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.7.dfsg.1-0ubuntu5.1_i386.deb
  Size mismatch


W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.7+2.7.7.dfsg.1-0ubuntu5.1_i386.deb
  Size mismatch



```

could you please give a 'quick' how to, with the gdeb thing you did

Ta

In the 1st post click on the links 1 at a time 
A gdeb box opens up click install you will get some more boxes popup just closes them and do the install
1 at a time . good luck

---

### Post by Evagrios on 2008-11-20
Same problem, this does not help.

---

### Post by jryprt on 2008-11-20
Iam using 7.10 Gusty.

---

### Post by lightnin on 2008-11-20
Thanks - that seems to have worked - my system is now up to date :)

so ...

1.  I clicked the links you gave, but dont know how I would do it if your links weren't there.

2.  Should this be reported as a bug ?

---

### Post by lightnin on 2008-11-20
> **jryprt said:**
> Iam using 7.10 Gusty.

me too

---

### Post by Thrasyllus on 2008-11-20
> **jryprt said:**
> In the 1st post click on the links 1 at a time 
A gdeb box opens up click install you will get some more boxes popup just closes them and do the install
1 at a time . good luck
Thanks for posting this. In what directory should the HPIP files go?

---

