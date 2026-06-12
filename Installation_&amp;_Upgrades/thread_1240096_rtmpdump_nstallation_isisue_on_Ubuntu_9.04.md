---
title: "rtmpdump nstallation isisue on Ubuntu 9.04"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by harry2006 on 2009-08-14
i was trying to instal rtmpdump in Ubuntu 9.04 by compiling the source code, i got the source code from the main source[[http://lkcl.net/rtmp/]](http://lkcl.net/rtmp/]) and then trying to compile as per the instructions gave me a bunch of errors like this:


harry@harry-laptop:~/softies/socs/rtmpdump$ make rtmpdump
g++ -Wall   -c -o rtmp.o rtmp.cpp
In file included from rtmp.h:43,
                 from rtmp.cpp:36:
dh.h:21:24: error: openssl/bn.h: No such file or directory
dh.h:22:24: error: openssl/dh.h: No such file or directory
dh.h:24:25: error: openssl/sha.h: No such file or directory
dh.h:25:26: error: openssl/hmac.h: No such file or directory
dh.h:26:25: error: openssl/rc4.h: No such file or directory
In file included from rtmp.h:43,
                 from rtmp.cpp:36:
dh.h:30: error: ‘BIGNUM’ was not declared in this scope
dh.h:30: error: ‘y’ was not declared in this scope
dh.h:30: error: ‘BIGNUM’ was not declared in this scope
dh.h:30: error: ‘p’ was not declared in this scope
dh.h:30: error: ‘BIGNUM’ was not declared in this scope
dh.h:30: error: ‘q’ was not declared in this scope
dh.h:30: error: initializer expression list treated as compound expression
dh.h:31: error: expected constructor, destructor, or type conversion before ‘*’ token
dh.h:32: error: ‘DH’ was not declared in this scope
dh.h:32: error: ‘dh’ was not declared in this scope
dh.h:33: error: ‘DH’ was not declared in this scope
dh.h:33: error: ‘dh’ was not declared in this scope
dh.h:33: error: expected primary-expression before ‘*’ token
dh.h:33: error: ‘pubkey’ was not declared in this scope
dh.h:33: error: expected primary-expression before ‘nPubkeyLen’
dh.h:33: error: initializer expression list treated as compound expression
dh.h:34: error: ‘DH’ was not declared in this scope
dh.h:34: error: ‘dh’ was not declared in this scope
dh.h:34: error: expected primary-expression before ‘*’ token
dh.h:34: error: ‘privkey’ was not declared in this scope
dh.h:34: error: expected primary-expression before ‘nPrivkeyLen’
dh.h:34: error: initializer expression list treated as compound expression
dh.h:35: error: ‘DH’ was not declared in this scope
dh.h:35: error: ‘dh’ was not declared in this scope
dh.h:35: error: expected primary-expression before ‘*’ token
dh.h:35: error: ‘pubkey’ was not declared in this scope
dh.h:35: error: expected primary-expression before ‘nPubkeyLen’
dh.h:35: error: expected primary-expression before ‘*’ token
dh.h:35: error: ‘secret’ was not declared in this scope
dh.h:35: error: initializer expression list treated as compound expression
dh.h:36: error: variable or field ‘DHFree’ declared void
dh.h:36: error: ‘DH’ was not declared in this scope
dh.h:36: error: ‘dh’ was not declared in this scope
In file included from rtmp.cpp:36:
rtmp.h:94: error: ISO C++ forbids declaration of ‘DH’ with no type
rtmp.h:94: error: expected ‘;’ before ‘*’ token
rtmp.h:95: error: ISO C++ forbids declaration of ‘RC4_KEY’ with no type
rtmp.h:95: error: expected ‘;’ before ‘*’ token
rtmp.h:96: error: ISO C++ forbids declaration of ‘RC4_KEY’ with no type
rtmp.h:96: error: expected ‘;’ before ‘*’ token
rtmp.cpp: In member function ‘int RTMP_LIB::CRTMP::ReadN(char*, int)’:
rtmp.cpp:450: error: ‘struct RTMP_LIB::LNK’ has no member named ‘rc4keyIn’
rtmp.cpp:451: error: ‘struct RTMP_LIB::LNK’ has no member named ‘rc4keyIn’
rtmp.cpp:451: error: ‘RC4’ was not declared in this scope
rtmp.cpp: In member function ‘bool RTMP_LIB::CRTMP::WriteN(const char*, int)’:
rtmp.cpp:469: error: ‘struct RTMP_LIB::LNK’ has no member named ‘rc4keyOut’
rtmp.cpp:471: error: ‘struct RTMP_LIB::LNK’ has no member named ‘rc4keyOut’
rtmp.cpp:471: error: ‘RC4’ was not declared in this scope
make: *** [rtmp.o] Error 1
harry@harry-laptop:~/softies/socs/rtmpdump$ 


seems something is missing. I've openssl, btw. 
Can someone let me know what exactly is the issue? How to fix the problem. I need rtmpdump to use for the utility get_flash_videos for downloading videos from videolectures.net. thank you.

---

### Post by idono on 2009-08-14
You need libssl-dev and libboost-dev to compile rtmpdump.

---

