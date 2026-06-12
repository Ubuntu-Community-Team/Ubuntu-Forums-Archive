---
title: "Need help setting up HP psc 1350 printer drivers"
date: 2005-12-18
forum: Hardware &amp; Laptops
---

### Post by TrinitronX on 2005-12-18
Ok.. so far I've followed HP's instructions for installing their linux drivers for my printer/scanner/copier.  The problem is that when trying to add a printer during this step: [http://hpinkjet.sourceforge.net/install.php#print_queue](http://hpinkjet.sourceforge.net/install.php#print_queue)
I cannot log in to it using either root or my login and their respective passwords.
Any ideas?

---

### Post by kairu0 on 2005-12-18
Substitute, "su" in that guide for the following:

```
sudo -s
```

---

### Post by sarah_b on 2005-12-18
Hi TrinitronX

The 1350 is an all-in-one correct ?

All you should have to do in that case is open Synaptic Package Manager, do a search for "hpijs" and download it. Then go to System > Administration > Printing and when adding printer choose other and go from there. If I remember correctly, use the PCI 1310 driver, that should work if it is indeed an all-in-one.

I hope this works for you, sarah

---

### Post by TrinitronX on 2005-12-21
thanks... I have it all set up now :D

---

