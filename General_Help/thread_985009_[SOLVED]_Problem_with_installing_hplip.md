---
title: "[SOLVED] Problem with installing hplip"
date: 2008-11-17
forum: General Help
---

### Post by pumex1990 on 2008-11-17
Hi, 
I downloaded hplip-2.8.5.run, and when run it, during the insallation I'm getting this infomation:

```
INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 6 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

```

So i'm trying to install gcc by typing sudo apt-get install gcc, but it shows that it's already installed.

What should I do to install hplip?

---

### Post by drs305 on 2008-11-17
hplip version 2.8.7 is in synaptic (at least in Intrepid). Is there a specific reason you can't use that one (or whichever version is in your synaptic listings)?

---

### Post by pumex1990 on 2008-11-17
Ok, I solved my problem with hplip and printer (I had something messed up with my repository list)

Thanks :)

---

