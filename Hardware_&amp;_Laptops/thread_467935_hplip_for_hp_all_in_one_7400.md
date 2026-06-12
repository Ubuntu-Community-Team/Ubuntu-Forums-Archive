---
title: "hplip for hp all in one 7400"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by tamera on 2007-06-08
I'm very new to ubunti (yesterday). Feisty Faun amd64. I'm trying to add hplip and from forums, it seems the error message that I'm getting might be due to not having build-essential. I tried to add it using synaptic manager and it failed. I also tried the following lines from another post

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential


, but get the following messages:

Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-0ubuntu4_amd64.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-0ubuntu4_amd64.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/pool/main/g/gcc-defaults/g++_4.1.2-1ubuntu1_amd64.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Any advice? Perhaps I'm going down the wrong track to add hplip? The error message I'm getting there is 
configure: error: C compiler cannot create executables

Thanks for any help!

---

### Post by NewJack on 2007-06-08
HPLIP is in the repositories.  Try adding it from there, I believe it is the latest release.  Just do a search for "HPLIP" and you'll find it.

---

