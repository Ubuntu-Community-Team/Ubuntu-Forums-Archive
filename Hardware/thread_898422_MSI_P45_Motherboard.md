---
title: "MSI P45 Motherboard"
date: 2008-08-23
forum: Hardware
---

### Post by jett on 2008-08-23
I just bought an [MSI P45 motherboard ]("http://global.msi.com.tw/index.php?func=proddesc&prod_no=1479&maincat_no=1&cat2_no=170").

First thing I tried was to see if I could run the Hardy LiveCD. During the bootup, it stops and shows the BusyBox prompt.

Anyone else has this board and found a way to get Hardy to work?

---

### Post by coffeecat on 2008-08-23
I have no experience with this board, but I've seen threads where people are having trouble with boards of other makes with the P45 chipset.

It might be worth searching the forum for 'P45' to see if you can find a fix.

---

### Post by jett on 2008-08-24
did some searching, it looks like kernel 2.6.26 has support for the P45 chipset and ICH10. will try to create a custom install cd with the newer kernel image

---

### Post by jett on 2008-09-09
haven't tried recompiling a custom kernel for the LiveCD yet but ... I was successfully able to boot and install CentOS 5.2 on the same machine. 

It uses kernel 2.6.18 which means it may just be a matter of recompiling ...

---

### Post by jett on 2008-09-21
Update ...

I decided to try an easier route. (Well, technically the easier Ubuntu route since I was able to get CentOS 5.2 to run on it).

 Was able to boot of the Intrepid Alpha 6 LiveCD so I guess getting it to work on the P45 is a kernel support issue. Network and sound are working but it looks like the binary ATI drivers cannot be installed on Intrepid (yet).

Will still attempt to create a LiveCD with a kernel patched with ICH10 support. Had no problems patching/compiling the kernel but couldn't get it to work in a LiveCD (it stops at the BusyBox prompt).

---

