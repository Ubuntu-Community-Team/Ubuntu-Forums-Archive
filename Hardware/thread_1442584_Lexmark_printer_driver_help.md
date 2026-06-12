---
title: "Lexmark printer driver help"
date: 2010-03-30
forum: Hardware
---

### Post by _simon_ on 2010-03-30
Does this mean it won't work with 64bit Ubuntu?

```

simon@simon-desktop:~$ sudo '/home/simon/lexmark-08z-series-driver-1.0-1.i386.deb.sh' 
[sudo] password for simon: 
Verifying archive integrity... All good.
Uncompressing nixstaller..............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
./startupinstaller.sh: 169: bin/linux/x86/libc.so.6/lzma-decode: not found
Error: Couldn't find any suitable frontend for your system

```

---

### Post by _simon_ on 2010-03-30
Managed to start the installer with 

```

sudo --force

```

However, after the first few screens it's asks for the Admin password and no matter how many times I enter it, it tells me it's incorrect.

---

