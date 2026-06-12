---
title: "Memory Stick Pro Duo doesn't work"
date: 2009-06-03
forum: Hardware
---

### Post by dfienberg on 2009-06-03
Hi

When I insert my Memory Stick Pro Duo nothing happens. It works in Windows so there isn't anything wrong with the card or reader. The reader, however does work from SD cards. I'm running Ubuntu 8.10 on an Acer Aspire 5630.

---

### Post by cyrus_SR on 2009-06-03
> **dfienberg said:**
> Hi

When I insert my Memory Stick Pro Duo nothing happens. It works in Windows so there isn't anything wrong with the card or reader. The reader, however does work from SD cards. I'm running Ubuntu 8.10 on an Acer Aspire 5630.

Show ```
lspci | grep Stick
```

---

### Post by dfienberg on 2009-06-04
When I type ```
lspci | grep Stick
``` in the terminal, the following is my output.
```
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
```

---

### Post by MSToTheEnd on 2009-06-05
I'm having the same problem. But as far as I know there's no solution available for this. :S

---

### Post by cyrus_SR on 2009-06-05
dfienberg
> **MSToTheEnd said:**
> I'm having the same problem. But as far as I know there's no solution available for this. :S
I know one
> svn co -r155 [http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/](http://svn.berlios.de/svnroot/repos/tifmxx/trunk/driver/)
cd driver/
wget [http://www.tu-chemnitz.de/~sweh/tifm_ms.patch]("http://www.tu-chemnitz.de/%7Esweh/tifm_ms.patch")
patch -p0 < tifm_ms.patch
make
sudo make installbut it's only for Texas Inc. readers. =(

---

### Post by dahc2424 on 2009-06-05
> **MSToTheEnd said:**
> I'm having the same problem. But as far as I know there's no solution available for this. :S

I am having the same problem and have found no solution.

---

