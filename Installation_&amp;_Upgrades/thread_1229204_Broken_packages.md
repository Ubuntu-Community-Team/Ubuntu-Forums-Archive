---
title: "Broken packages"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by cquigley on 2009-08-01
Hi Everyone-

  I finally found out why I could not install some apps.  I ran "gksudo synaptic" and found out that I have to broken packages. Below are the broken packages. This is word for word how synaptic showed the broken packages when I used the broken filter. I am running Jaunty 9.04.

 1. **Package** - linux-image-generic
     **Installed ver**. - 2.6.28.14.19
     **Latest Ver.** - 2.6.28.14.19
     **Description** -  Generic Linux kernel 

2.** Package** - image linux-restricted-modules-2.6.28-14-generic 
    **Installed Ver.** - 2.6.28-14.19
    **Latest Ver.** - 2.6.28-14.19
    **Description** - Non-free Linux kernel modules for version 2.6.28 on x86/x86_64

I cannot figure out how to fix these. Please any help would be great.

thanks,
 cquigley

---

### Post by cquigley on 2009-08-01
Got It working

---

### Post by spribo on 2009-08-03
I have the same problem... could you say how you solved it please?

---

### Post by Partyboi2 on 2009-08-03
> **spribo said:**
> I have the same problem... could you say how you solved it please?
To fix broken packages you can open up a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get -f install
```
or open Synaptic (System>Admin>Synaptic) and go to Edit>Fix Broken Packages.

---

### Post by spribo on 2009-08-03
They don't work. It finds error instead:
E: /var/cache/apt/archives/linux-image-2.6.28-14-generic_2.6.28-14.47_i386.deb: &#951; &#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945; pre-installation script &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#955;&#940;&#952;&#959;&#965;&#962; 1

---

### Post by Partyboi2 on 2009-08-03
Can you post the whole output to
```
sudo apt-get -f install
``` hopefully this will provide further information on what the problem is.

---

### Post by spribo on 2009-08-03
Well, after rebooting "sudo apt-get -f install" did work! Thanks for your help!

---

