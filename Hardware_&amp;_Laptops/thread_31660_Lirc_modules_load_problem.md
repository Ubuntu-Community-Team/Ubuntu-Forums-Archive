---
title: "Lirc modules load problem"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by natarajmb on 2005-05-04
Hi

  I just compiled modules from source. I have a serial reciver. I have done this setting up before in debian sarge and worked with out problems but with no success in Ubuntu. This is what i have done

    Installed linux-source-2.6.10 and lirc-modules-source
    reconfigured lirc-modules-source.conf to include serial support
    compiled modules based on README in lirc folder. I used make-kpkg
    to make modules. I had a .deb package in source directoty installed the
   modules and modules are installed in right place. i.e in                                                      
   /lib/modules/2.6.10-5-686-smp/misc/ after this updated modules. if try to insert
   module with modprobe i get this error
                                   FATAL: Module lirc_serial not found.
   I am using a stock linux-image-2.6.10-5-686-smp from ubuntu source.
   any help apprecitaed....

thanks

---

### Post by danbee on 2005-05-04
The lirc-modules-source package appears to default to compiling modules for 2.4 kernels (.o) rather than modules for a 2.6 kernel (.ko).  There is a guide here -> [http://www.ubuntuforums.org/showthread.php?t=30612&highlight=lirc](http://www.ubuntuforums.org/showthread.php?t=30612&highlight=lirc)

---

