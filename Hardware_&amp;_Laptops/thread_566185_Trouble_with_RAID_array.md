---
title: "Trouble with RAID array"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by JamNCheez on 2007-10-03
I recently got fed up with windows and decided to go down the ubuntu (Feisty) route and so far I like what I see, I've managed to get pretty much everything up and running.

My problem is this, I have a NTFS hardware RAID 0 array which contains about 300gig of media which windows can read fine, but ubuntu doesn't seem to notice it. So I dug out the drivers disc an lo and behold there are linux drivers - but alas only for redhat or mandrake. I read somwhere that something called Alien is good for converting to debian drivers, but I don't really know what I'm doing so some pointers in the right direction very helpful. File listing of the drivers directory is given below:


```
    +- md90			Mandrake 9.0 directory
    |  |- iteraid.o		Driver module for Mandrake 9.0
    |
    +- rh73			RedHat 7.3 directory
       |- modinfo		Module info file
       |- modules.cgz		Compressed driver modules
       |- modules.dep		Module dependence file
       |- pcitable		IT8212 pci info
       |- rhdd-6.1		Driver disk label
       |- iteraid.o		Driver module for RedHat 7.3
```


Many thanks!

---

### Post by JamNCheez on 2007-10-04
I've still got nowhere with this, though I did find some resources: there's a copy of the cd i have at [http://tinyurl.com/2jbfpp]("http://tinyurl.com/2jbfpp") but tbh I think it's a lost cause. A friend of mine says they are very old and unlikely to work with newer kernels

---

