---
title: "Configuring Softwares"
date: 2008-08-31
forum: General Help
---

### Post by Alipacino on 2008-08-31
Hi
I'm so new to ubuntu (and generally linux) and i have a problem with configuring softwares
when i try to configure a software (for now: downloader for X) i get this error:

```
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
```

i have the same problem with some other softwares.
is there anything else i should download and install before these softwares? please help me
thanks in advance

---

### Post by aloshbennett on 2008-08-31
What are you doing and how are you doing it?

From the log you sent, looks like the script is trying to compile onto /usr/bin/install and you dont have write permissions on the folder. Can you try the same with sudo?

---

### Post by kellemes on 2008-08-31
In order to compile packages you need to install the following first..
```
sudo apt-get install build-essential
```

---

### Post by Alipacino on 2008-09-06
well thanks it worked and solved this problem
but now i have another:
it was configured successfully and makefiles have been created in the directory but when i do the "make" it says:
No targets specified and no makefile found.
what should i do now?

---

### Post by zvacet on 2008-09-06
Why don´t you install** d4x **from synaptic?

---

