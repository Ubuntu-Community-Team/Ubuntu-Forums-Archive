---
title: "What are the benefits of installing the 64bit version of ubuntu?"
date: 2008-11-26
forum: General Help
---

### Post by maduranga on 2008-11-26
I need to install ubuntu and don't know which one to go with (32bit vs 64bit) I have core 2 duo 2.2Ghz and 4GB of ram. Are there any benefits of using 64bit over 32bit? will there be a lack of softwares etc?

---

### Post by FSXmann on 2008-11-26
I believe a 64-bit architecture is able to handle up to 8GB of RAM, while 32-bit can only handle a little less than 4GB. Most dual-core processors can support a 64-bit OS, so I would go for it. All regular applications should still work just fine. The main difference is that the 64-bit version should be better able to utilize all your system's RAM.

---

### Post by philinux on 2008-11-26
If say you have a 512meg graphics card then that needs to be addressed so your 4gig already becomes 3.5 under 32bit. Not so with 64 bit.

Also read this.
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)
Update. A 64 bit flash alpha is now available so no worries with flash or java.

64 bit can access Terabytes of ram . cant remember the exact figure but it's huge.

---

### Post by sdennie on 2008-11-26
> **philinux said:**
> 
64 bit can access Terabytes of ram . cant remember the exact figure but it's huge.

The 64bit address space should be able to addres up to 16 exabytes of memory (that's a lot) however, both hardware and software limitations make this number much lower in practice.  At least on AMD chips, you can only address up to 32 terabytes of RAM on 64bit and the kernel imposes a restriction at 64 terabytes (I think).  You can actually use all 4G of RAM on a 32bit machine but you need to enable PAE in the kernel.  This link has some more information about Ubuntu with 4GB+ of RAM: [http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

---

### Post by Guilden_NL on 2008-11-26
IMHO, the more people use 64 bit Linux _**and/or**_ Windows, the more SW providers will wake up and smell the dead market for 32 bit apps.  Each and every opportunity to bring folks to the 64 bit world is golden. :)

---

### Post by maduranga on 2008-11-28
> **Guilden_NL said:**
> IMHO, the more people use 64 bit Linux _**and/or**_ Windows, the more SW providers will wake up and smell the dead market for 32 bit apps.  Each and every opportunity to bring folks to the 64 bit world is golden. :)

thanks. I've been already using 64 bit vista. just wanted to know the better option for ubuntu!

---

