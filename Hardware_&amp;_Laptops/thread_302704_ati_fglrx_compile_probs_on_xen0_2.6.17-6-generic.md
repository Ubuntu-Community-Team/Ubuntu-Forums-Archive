---
title: "ati fglrx compile probs on xen0 2.6.17-6-generic"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by glenndavy on 2006-11-19
Hi All 
Im trying to follow this guide, and hitting probs when it comes to doing the build:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Kernel:2.6.17-6-generic-xen0

```

m-a build fglrx 

```

Gives this error:
```

touch configure-stamp   
                                                   
 dh_testdir                                                                  
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules     

make[1]: Entering directory `/usr/src/xen-headers-2.6.17-6-generic-xen0'   

WARNING: Symbol version dump                                             

 /usr/src/xen-headers-2.6.17-6-generic-xen0/Module.symvers                  

 is missing; modules will have no dependencies and modversions.  

  ln: creating symbolic link `./Makefile.lib.c' to                           
 `../scripts/Makefile.lib.c': File exists
   make[2]: *** [scripts/Makefile.lib.c] Error 1   
   make[1]: *** [_module_/usr/src/modules/fglrx] Error 2 
   make[1]: Leaving directory `/usr/src/xen-headers-2.6.17-6-generic-xen0'     
   make: *** [build] Error 2      

```

works fine for 2.6.17-10-generic however.

any ideas?

thanks

---

