---
title: "Memory not reading correctly"
date: 2010-12-05
forum: Hardware
---

### Post by MadJestyr on 2010-12-05
I am having a problem. 
I just added 4Gb (2x2Gb)of ram to my system with 2Gb (2x1Gb) already installed. The Bios detects the memory just fine, during boot up it registers 6143Mb of memory, and in the setup it reads each stick correctly.  
Problem is, when I boot into Ubuntu and go to my system monitor it only tells me that I have 3.2Gib of memory.  :?

What do I do?

---

### Post by MadJestyr on 2010-12-05
bump

---

### Post by MadJestyr on 2010-12-05
Help?

---

### Post by 73ckn797 on 2010-12-05
Are you running 32 bit or 64 bit Ubuntu? 64 bit should see the memory. 32 bit will require the PAE kernel from the repositories. PAE = Physical Address Extension. I have 6GiB RAM on one computer running the 32 bit Ubuntu and use the PAE kernel. It reads it as 5.9GiB.

---

