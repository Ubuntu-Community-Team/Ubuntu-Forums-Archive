---
title: "install ATI driver"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by strumica on 2007-12-21
I have fresh install of Gutsy on my laptop, and I can not start my ATI driver in the restricted drivers manager. I get the error:

"The software source for the package

   xorg-driver-fglrx

 is not enabled."

I have this problem for a while now, but I have been using ENVY so it might messed up the things a little bit. Now I have only fresh installed Gutsy, nothing touched. 
Please help.

Hardware:
Acer Aspire 5100
AMD Turion 3000+
1GB RAM
ATI Radeon X1100

---

### Post by hedgebox on 2007-12-21
Check out [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by strumica on 2007-12-21
OK, tried that, and here is the result:

The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages

---

### Post by kelvin spratt on 2007-12-21
Open synaptic click on custom filters then broken packages and remove any broken packages before you try anything else.  Then turn all eye candy off and then try to update your drivers, then post back.

---

### Post by strumica on 2007-12-21
Broken Packages list empty

---

