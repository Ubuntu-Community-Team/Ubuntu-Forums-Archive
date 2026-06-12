---
title: "VMWare tools (version.h missing)"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by bas_vdl on 2009-03-24
i tried to install and configure vmware tools.

i installed the tools, but when i want to configure them it fails.

first i had to install a compiler by running apt-get install build-essentials.

then i tried it again (/usr/bin/vmware-config-tools.pl), but now the configuring tools was asking for my kernel hearders files.

so i installad my headers files by doing this: apt-get install linux-headers-2.6.27-7-server.

now i have two directories in /usr/src/. linux-headers-2.6.27-7 and linux-headers-2.6.27-7-server.

then i runned the /usr/bin/vmware-config-tools.pl again and point the install to de headers file location. but it fails.

"the path "/user/src/linux-headers-2.6.27-7-server/include" is a kernel header file director, but it does not contain the file "linux/version.h" as expected."

i tried the make 'mrproper command' but still no version.h file...

i need some help

thank you

---

### Post by veloce on 2009-03-31
> **bas_vdl said:**
> i tried to install and configure vmware tools.

i installed the tools, but when i want to configure them it fails.

first i had to install a compiler by running apt-get install build-essentials.

then i tried it again (/usr/bin/vmware-config-tools.pl), but now the configuring tools was asking for my kernel hearders files.

so i installad my headers files by doing this: apt-get install linux-headers-2.6.27-7-server.

now i have two directories in /usr/src/. linux-headers-2.6.27-7 and linux-headers-2.6.27-7-server.

then i runned the /usr/bin/vmware-config-tools.pl again and point the install to de headers file location. but it fails.

"the path "/user/src/linux-headers-2.6.27-7-server/include" is a kernel header file director, but it does not contain the file "linux/version.h" as expected."

i tried the make 'mrproper command' but still no version.h file...

i need some help

thank you

Check that the headers you are trying to use are consistent with the output of:

```
uname -r
```

---

