---
title: "Fingerprint Reader Installation Error: malloc"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by rgmussel on 2006-04-16
I am trying to install the fingerprint reader for an IBM Z60t. I have followed instructions from both [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader") and [http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_fingerprint_reader]("http://linux.spiney.org/debian_gnu_linux_on_an_ibm_thinkpad_t43p_fingerprint_reader"). I've found the second to be more useful than the second, except that neither process has actually worked for me. 

When trying to compile the Sample file, I get the following:

# gcc -o Sample main.c -L/usr/local/lib -lbioapi100 -DUNIX -DLITTLE_ENDIAN main.c: In function 'main':
main.c:97: warning: incompatible implicit declaration of built-in function 'malloc'
main.c: In function 'SetToBSP':
main.c:409: warning: incompatible implicit declaration of built-in function 'malloc'
main.c:420: warning: incompatible implicit declaration of built-in function 'exit'
main.c:434: warning: incompatible implicit declaration of built-in function 'exit'
main.c: In function 'InputFromFile':
main.c:504: warning: incompatible implicit declaration of built-in function 'malloc'

I understand that "malloc" is a memory allocation process, complete with a man page. However, I can't seem to find anywhere that I can install it from. Any suggestions about how to get around this problem?

Thanks!

---

### Post by spotslayer on 2006-10-28
Was there ever any suggestions to correct this? I am have the same thing on my N200. I have followed the two howto's listed in these forums but can't get past this.

David

---

### Post by reptil on 2007-01-19
hi spotslayer and rgmussel.
i 've the same problem did u have  the solution... can u helpme ...

thank's

---

### Post by reptil on 2007-01-23
hi 
in order to correct those warnnings u must add this line  #include <stdlib.h>
that's all...
now... afther compile, uncommentted BioAPI_SetGUICallbacks and run ./Sample i've the next error :
main.c:137: warning: passing argument 4 of ‘BioAPI_SetGUICallbacks’ from incompatible pointer type

we will dismiss it changing TextGuiCallback by NULL.... now compile and run ./Sample

and sorprise i've a new error tBIOAPIBioAPI_ModuleLoad failed, BioAPI Error Code: 6477 (0x194d)

someone can helpme ?? 

ubunto edgy eft
fingerprint reader touchchip
TFMESS BioAPI BSP for Linux

---

### Post by prdatur on 2008-06-09
Hey all,

Have same Notebook, Same problem.
IBM Lenovo 3000 N200

Got the same problem 

```

./Sample 
Starting Sample Application
Major=1 Minor=10
BSP Index= 0
BSP Name: libbioapi_dummy100.so
Description: BioAPI v1.1 Dummy BSP
Vendor: Example Vendor
Module ID: {ffffffffffffffffffffffffffffffff}
Device ID: 0x00000000
BSP Index= 1
BSP Name: libpwbsp.so
Description: BioAPI Password BSP
Vendor: BioAPI Consortium
Module ID: {263a41e071eb11d49c34124037000000}
Device ID: 0x00000000
BSP Index= 2
BSP Name: libtfmessbsp.so
Description: TouchChip TFM/ESS Fingerprint BSP
Vendor: UPEK, Inc.
Module ID: {5550454b2054464d2f45535320425350}
Device ID: 0x00000000
BioAPI_ModuleLoad failed, BioAPI Error Code: 6477 (0x194d)

```

anyone have solutions ?

greets prdatur

---

