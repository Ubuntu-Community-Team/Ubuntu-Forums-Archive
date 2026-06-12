---
title: "scsi adapter sym53c416"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by ivolinux on 2007-07-20
I have big problem with my scanner HP scanjet 5p 
Old kernel 2.4 the scanner work very well,  it need just to load the SCSI module sym53c416 before to open xsane.
if type modprobe sym53c416  with kubuntu 7.04 I obtain an error (impossible found sym53c416.ko).
I tried a lot of disto form debian 4 to fedora 7 but all distro give me the same problem!
I have compiled the kernel by myself  I followed this instruction [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
I have putted the modules inside the kernel, (not  like a module). 
The kernel work very well, but :
 lsmod -> not kernel in the list
 modprobe -> fatal error
find / -name sym53c416.ko  -> nothing 
SO any idea? I need a new scanner
PS the scanner work very fine wit windows sigh
thanks in advance ](*,)](*,)]

---

