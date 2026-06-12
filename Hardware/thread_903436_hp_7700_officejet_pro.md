---
title: "hp 7700 officejet pro"
date: 2008-08-28
forum: Hardware
---

### Post by pixideps on 2008-08-28
Sorry I am rather new and maybe I am asking a stupid thing but I wonder how to install hp 7700 officejet pro as scanner - since seller nor hp provide any drivers for linux. I've managed to install it as printer but .. scanning option still missing
thanx in advance

---

### Post by phidia on 2008-08-28
Welcome to Ubuntu!
The SANE site reports [your device]("http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=officejet+pro+7700&bus=any&v=&p=") as working so that's good.
Have you installed the hplip package? It seems like that all you should need.
Either use the package manager Synaptic and search for the hplip package (System >Admin > Synaptic).

Or in a terminal enter > sudo apt-get install hplip After that you should find a HP gui under your system menu. You can configure or use the scanner function from that.

---

### Post by silvanus2005 on 2008-08-28
You can  also instal HPLIP using Synaptic Package Manager.

---

### Post by pixideps on 2008-09-01
Great 
thanx a lot. Now I've realized that I had hplip but did not have gui.
Great once again
:guitar::lolflag::KS:)

---

