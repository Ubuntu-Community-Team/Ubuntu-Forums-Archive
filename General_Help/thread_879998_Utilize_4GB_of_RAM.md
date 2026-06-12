---
title: "Utilize 4GB of RAM"
date: 2008-08-04
forum: General Help
---

### Post by CarlosinFL on 2008-08-04
I just installed Ubuntu for a test drive after using Debian Lenny for 2 years. It seems OK however according to the standard kernel I am running, it does not appear to have the module loaded to utilize more than 3.2GB's of RAM. Under Debian I was able to install **linux-image-2.6.25-2-686-bigmem** which was able to utilize all 4GB's of RAM. There does not appear to be anything I can find for Ubuntu which I find shocking. I understand that 64 bit users / kernels will work but I am using a 32 bit machine. 

Anyone know if there is a way to get this to work or if there is a big-mem modified kernel for Ubuntu?

```
cwilliams@tunafish:~/Desktop$ uname -r
2.6.24-19-generic

```

---

### Post by blazercist on 2008-08-04
I don't know if there are any images in the repos for "big-mem" kernels, but you could always compile your own... or switch to 64-bits but I'm sure you don't want to do that.  There are patches for the vanilla 32-bit kernels that give support for extra memory.

---

### Post by CarlosinFL on 2008-08-04
I can't run 64 sadly so that is not an option and I don't see anything in the apt-cache search mirrors.

What do you mean there are "patches" for 32 bit kernels? 

I have never compiled a kernel since I have only used Debian and never had a need to. They seem to have every different kernel known to man available.

---

### Post by MrHippocampus on 2008-08-04
I'm not 100% sure but I think the linux-image-2.6.xx-xx-server kernels have the bigmem stuff in them

---

### Post by tamoneya on 2008-08-04
there is a patch and it is called physical address extension or PAE.

[http://ubuntuforums.org/showthread.php?p=5373592](http://ubuntuforums.org/showthread.php?p=5373592)

---

### Post by mrmorris on 2008-08-04
Few motherboards supports PAE. I have a recent motherboard, 64bit CPU and 64bit Ubuntu but have never been able to utilize more than 3.2GB. I believe it's a chipset issue.

---

### Post by Vivaldi Gloria on 2008-08-04
Installing the server kernel should do it. Look for something like

linux-image-2.6.24-18-server

---

