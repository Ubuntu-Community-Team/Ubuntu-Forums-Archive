---
title: "java issue with installing Oracle9i on Ubuntu 8.04"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by leendertn on 2009-05-11
No matter what version of JRE I use, this will not install. If I use the sun-jave-6 version of JRE I get all the pretty Oracle windows, but when it gets to the actual install portion, it never goes past the linking JRE 1.1.8....

If I use the jre version that is in the oraparam.ini file I get this:

Initializing Java Virtual Machine from /tmp/OraInstall2009-05-11_08-32-33AM/jre/bin/java. Please wait...
/tmp/OraInstall2009-05-11_08-32-33AM/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
These are the libraries I have:

oracle@csgentoo:~/Oracle9i/Disk1/install/linux$ apt-cache search libstdc
libstdc++5-3.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++5-3.3-dev - The GNU Standard C++ Library v3 (development files)
libstdc++5-3.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++5-3.3-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-pic - The GNU Standard C++ Library v3 (shared library subset kit)
lib64stdc++6 - The GNU Standard C++ Library v3 (64bit)
lib64stdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-4.2-dbg - The GNU Standard C++ Library v3 (debugging files)
lib64stdc++6-4.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libgmp3-dev - Multiprecision arithmetic library developers tools
libstdc++5 - The GNU Standard C++ Library v3
libstdc++6 - The GNU Standard C++ Library v3
libstdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.1-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.1-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.1-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.2-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.2-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.2-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.2-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.3-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-4.3-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++2.10-glibc2.2 - The GNU stdc++ library

I have tried to use a symbolic link but that gets me a segmention fault

I have  2 other servers running 10g w/o problems (installed from scratch) but I need this version for some testing.

Thanks in advance for any suggestions.

---

