---
title: "sl-modem-source build fails"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by davidsrsb on 2007-08-13
Trying to build sl-modem-source fails.
I get
kernel-ver.c: In function ‘main’:                                          &#9618; 
 &#9474; kernel-ver.c:11: error: ‘UTS_RELEASE’ undeclared (first use in this        &#9618; 
 &#9474; function)                                                                  &#9618; 
 &#9474; kernel-ver.c:11: error: (Each undeclared identifier is reported only once  &#9618; 
 &#9474; kernel-ver.c:11: error: for each function it appears in.)                  &#9618; 
 &#9474; make[2]: *** [kernel-ver] Error 1                                          &#9618; 
 &#9474; make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'             &#9618; 
 &#9474; make[1]: *** [binary-modules] Error 2                                      &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/sl-modem'                     &#9646; 
 &#9474; make: *** [kdist_build] Error 2

---

