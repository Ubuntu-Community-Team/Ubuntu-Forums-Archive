---
title: "Ubuntu 8.10 CoWPAtty and Buffer Overflow Error"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by tomclark on 2009-01-03
Greetings,

I have installed CoWPAtty and am getting this error:

user@user-laptop:~/Desktop/wireless/cowpatty-4.3$ sudo ./cowpatty -r ssid_eapol.cap -f dict -s "ssid"
cowpatty 4.3 - WPA-PSK dictionary attack. <jwright@hasborg.com>

Collected all necessary data to mount crack against WPA/PSK passphrase.
Starting dictionary attack.  Please be patient.
*** buffer overflow detected ***: ./cowpatty terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d5e558]
/lib/tls/i686/cmov/libc.so.6[0xb7d5c680]
./cowpatty[0x804b307]
./cowpatty[0x804b5dc]
./cowpatty[0x804b708]
./cowpatty[0x8049e56]
./cowpatty[0x804a985]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7c7a685]
./cowpatty[0x8048cb1]
======= Memory map: ========
08048000-0804d000 r-xp 00000000 08:05 295904     /home/user/Desktop/wireless/cowpatty-4.3/cowpatty
0804d000-0804e000 r--p 00004000 08:05 295904     /home/user/Desktop/wireless/cowpatty-4.3/cowpatty
0804e000-0804f000 rw-p 00005000 08:05 295904     /home/user/Desktop/wireless/cowpatty-4.3/cowpatty
08a45000-08a66000 rw-p 08a45000 00:00 0          [heap]
b7c2c000-b7c39000 r-xp 00000000 08:05 2828958    /lib/libgcc_s.so.1
b7c39000-b7c3a000 r--p 0000c000 08:05 2828958    /lib/libgcc_s.so.1
b7c3a000-b7c3b000 rw-p 0000d000 08:05 2828958    /lib/libgcc_s.so.1
b7c49000-b7c4a000 rw-p b7c49000 00:00 0 
b7c4a000-b7c5e000 r-xp 00000000 08:05 2382823    /usr/lib/libz.so.1.2.3.3
b7c5e000-b7c60000 rw-p 00013000 08:05 2382823    /usr/lib/libz.so.1.2.3.3
b7c60000-b7c62000 r-xp 00000000 08:05 2846623    /lib/tls/i686/cmov/libdl-2.8.90.so
b7c62000-b7c63000 r--p 00001000 08:05 2846623    /lib/tls/i686/cmov/libdl-2.8.90.so
b7c63000-b7c64000 rw-p 00002000 08:05 2846623    /lib/tls/i686/cmov/libdl-2.8.90.so
b7c64000-b7dbc000 r-xp 00000000 08:05 2846617    /lib/tls/i686/cmov/libc-2.8.90.so
b7dbc000-b7dbe000 r--p 00158000 08:05 2846617    /lib/tls/i686/cmov/libc-2.8.90.so
b7dbe000-b7dbf000 rw-p 0015a000 08:05 2846617    /lib/tls/i686/cmov/libc-2.8.90.so
b7dbf000-b7dc3000 rw-p b7dbf000 00:00 0 
b7dc3000-b7ef5000 r-xp 00000000 08:05 2405335    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7ef5000-b7efd000 r--p 00132000 08:05 2405335    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7efd000-b7f0a000 rw-p 0013a000 08:05 2405335    /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7f0a000-b7f0e000 rw-p b7f0a000 00:00 0 
b7f0e000-b7f37000 r-xp 00000000 08:05 2382589    /usr/lib/libpcap.so.0.9.8
b7f37000-b7f38000 r--p 00028000 08:05 2382589    /usr/lib/libpcap.so.0.9.8
b7f38000-b7f39000 rw-p 00029000 08:05 2382589    /usr/lib/libpcap.so.0.9.8
b7f45000-b7f49000 rw-p b7f45000 00:00 0 
b7f49000-b7f63000 r-xp 00000000 08:05 2828915    /lib/ld-2.8.90.so
b7f63000-b7f64000 r-xp b7f63000 00:00 0          [vdso]
b7f64000-b7f65000 r--p 0001a000 08:05 2828915    /lib/ld-2.8.90.so
b7f65000-b7f66000 rw-p 0001b000 08:05 2828915    /lib/ld-2.8.90.so
bf950000-bf965000 rw-p bffeb000 00:00 0          [stack]
Aborted
user@user-laptop:~/Desktop/wireless/cowpatty-4.3$ 

Is anyone else experiencing this problem? If so, can you direct me to the fix?

Thanks a million,

Tom

---

### Post by jerg on 2009-09-11
I got the same isssue ....I will help look around for a solution and if i don't find any well then i'll try to understand the codes ....hey it'll be a learning experience :D.......

P.S. I notice that this post is date from Januaary 2009 so can you PM me if you found a solution already ....thanks in advance.....

---

### Post by jerg on 2009-09-17
Oh just upgrade to the 4.6 version of cowpatty ... I'm leaving this message just in case someone stumbles upon this thread from a google search

---

