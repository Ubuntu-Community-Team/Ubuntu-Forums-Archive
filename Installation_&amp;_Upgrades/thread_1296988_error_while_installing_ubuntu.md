---
title: "error while installing ubuntu"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by Sandersleutelslot on 2009-10-21
Hello, 
 I wanted to install ubuntu but when I had to choose and split partitions: 

 I had NTFS / dev/sda1 split in 2. 
 Allee, that is what I wanted ... 
 On the disk is also windows xp

 I also get this error when I use the GParted on the live CD to split ... 
 This avenue is in the details ... 
 there is a "mistake" to sign 
 Code: 

 Move / dev/sda1 to the left and shrink it from 73.10 GiB to 53.80 GiB 

 and when I click continue: 
 Code: 

 ```
shrink -> real resize -> (here the error apparently) ntfsresize-P - force - force / dev/sda1-s 57,766,109,183 
 -> Ntfsresize v2.0.0 (libntfs 10:0:0) 
 ERROR (95): Opening '/ dev/sda1' as NTFS failed: Operation not supported 
 using this software! Note, if you have previously run chkdslk then boot 
 Windows again which will automatically initialize the journal correctly. 

```

 and another error
```

 ntfsresize-P - force - force / dev/sda1 

```
 is again the same ... 
 file are in the details! 

 Does anyone know how I could have split or have to put ubuntu?? 

 Thanks very hard, 
 Sander

sorry for my bad english...

---

### Post by stlsaint on 2009-10-21
sorry but im not understanding your question..exactly what is it that you are wanting to do?

---

