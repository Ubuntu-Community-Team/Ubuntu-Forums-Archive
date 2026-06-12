---
title: "System can only see 3GB of RAM"
date: 2008-09-28
forum: Hardware
---

### Post by MrDiaz on 2008-09-28
As the title says, I have 4GB of RAM on my laptop but the System only recognizes 3GB. Anything I can do?

---

### Post by 98springer on 2008-09-28
I've been looking for this myself. Some posts recommend installing the Server kernel to break the ~3.5GB boundary and others mention using the PAE (Physical Address Extension?) kernel. I've used the latter many times with CentOS and Fedora but always Server installations. Will keep looking and post back. As far as I know, it should be possible.

---

### Post by 98springer on 2008-09-28
Well...I found this link in another post here.

[http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html)

---

### Post by jms1989 on 2008-09-29
One thing to note is, what is the max amount of ram does your mobo support? Some support 1GB, 2GB, 3GB, 4GB, or more. Depending on the mobo's compacity, it will depend on how much ram your os can use. If the mobo only supports 3GB, Ubuntu will only be able to see 3GB, regardless of kernel.

---

### Post by kingtaurus on 2008-09-29
Can you check in the BIOS to see if memory remapping is disabled?

Please post ```
 uname -a
```

---

### Post by craig.taverner on 2008-09-29
I'm having the same problem on Hardy 64-bit. From everything I've read I should see all my 6GB ram, but only see 3.2GB. Uname says: Linux lohri 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux.

I tried the server kernel, but still only saw 3GB, and also lost my screen resolution, so that was even worse. When I open the bios, The overview screen says there is 6GB. When I run the grum memtest, it only sees 3GB. When I boot linux (either generic or server kernels) I only see 3.2GB.

Any ideas?

---

### Post by craig.taverner on 2008-09-29
An update - I've now tried both the mem=6144M boot option and searched the bios for options to change. There were no bios options that sounded anything like memory remapping, and so I fiddled a few others with no luck. For reference, my computer is a packard-bell Imedia W1607 with Intel core2 quad and 6GB dual channel ddr2/667 (2x1GB and 2x2GB).

So, since so many others have got more than 3GB working by switching to 64bit, and I'm already on 64bit, I can only assume there is a problem between the kernel and this motherboard. What next can I do to track this down?

---

### Post by MrDiaz on 2008-09-29
yeah I tried the server kernel but that messed up my whole configuration. White screen after log in.

---

