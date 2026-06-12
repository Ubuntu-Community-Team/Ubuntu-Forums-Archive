---
title: "Adaptec 1045 SAS Driver compilation in 12.04"
date: 2012-09-14
forum: Hardware
---

### Post by kernal42 on 2012-09-14
Hi All,

I've installed the Adaptec 1045 SAS card in my desktop to communicate with a Tandberg LTO-3 HH Ultrium tape drive.  This is a setup I've gotten working in Fedora 9 (](*,)), but I'd really much prefer to operate the drive in Ubuntu 12.04.  There are no precompiled drivers for systems past kernel 2.6.*, but they provide source code (link below).  I've tried to compile this source code on my system running 3.2.0-29-generic x86_64, but get the failure:
```
make[2]: *** No rule to make target `arch/x86/tools/relocs.c', needed by `arch/x86/tools/relocs'.  Stop.
make[1]: *** [archscripts] Error 2

```

Is this something I can fix?  Perhaps I'm missing a package or have some environment variable path set wrong?

Thanks,
Kernal

[http://www.adaptec.com/en-us/downloads/linux_source/linux_source_code/productid=asc-1045&dn=adaptec+1045.html](http://www.adaptec.com/en-us/downloads/linux_source/linux_source_code/productid=asc-1045&dn=adaptec+1045.html)

---

