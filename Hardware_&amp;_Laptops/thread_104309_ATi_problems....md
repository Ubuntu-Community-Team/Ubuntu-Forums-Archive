---
title: "ATi problems..."
date: 2005-12-15
forum: Hardware &amp; Laptops
---

### Post by DJ Ubuntu on 2005-12-15
```
$  sudo module-assistant a-i fglrx


dh_testroot
                                &#9474; rm -f configure-stamp                                                      
                                &#9474; rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a                               
                                &#9474; rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd                        
                                &#9474; rm -rf .tmp_versions                                                       
                                &#9474; rm -rf patch                                                               
                                &#9474; dh_clean                                                                   
                                &#9474; rm /usr/src/modules/fglrx/debian/control                                   
                                &#9474; rm /usr/src/modules/fglrx/debian/dirs                                      
                                &#9474; if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \           
                                &#9474;         cat /usr/src/modules/fglrx/debian/control.template >               
                                &#9474; /usr/src/modules/fglrx/debian/control; \                                   
                                &#9474; fi                                                                         
                                &#9474; if [ -f postinst ]; then \                                                 
                                &#9474;         mv postinst fglrx-kernel-2.6.12-10-386.postinst; \                 
                                &#9474;
```

How that i solve it??.

Ubuntu 5.10 - 2.6.12-10-386

Help!

---

### Post by joshuapurcell on 2005-12-16
I'm not sure what problem you are having, or what you are trying to do with the above code. Post some error information and a description of the problem you are having, along with what you are trying to do.

There are some fglrx and radeon driver install howto's in the Tip's and Tricks forum if that's what you are needing help with.

---

