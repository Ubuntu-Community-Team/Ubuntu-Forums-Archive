---
title: "Trouble with ZSNES on Aspire One"
date: 2009-07-05
forum: Hardware
---

### Post by delsydebothom on 2009-07-05
Greetings, all!

I recently purchased an Acer Aspire One. Having read of several people getting ZSNES to work on theirs, I had hoped I could, too. But when I installed ZNES and tried to run it, nothing happened. Now when I click on something in Ubuntu, I'm used to things happening--sometimes good things, sometimes things less than good. In this case, though, it was as if the computer looked at the instruction I gave it and said, "Meh...I'll do it later." However, since the key to any good relationship is communication, I decided to take a look at the terminal, just to see what my machine might really be thinking. The result shocked and confused me, as it might you. Nevertheless, I am serious enough about getting ZSNES to work that I am going to share this with those on this forum, in hopes that one among you may be able to decipher this strange babble. Behold:

> *** glibc detected *** zsnes: munmap_chunk(): invalid pointer: 0xbf810f21 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7b7d604]
zsnes[0x80dd746]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7b24775]
zsnes(__gxx_personality_v0+0xcd)[0x804b9f1]
======= Memory map: ========
08048000-082f7000 r-xp 00000000 08:01 8880373    /usr/bin/zsnes
082f7000-0834a000 rwxp 002ae000 08:01 8880373    /usr/bin/zsnes
0834a000-085b6000 rwxp 0834a000 00:00 0 
094b6000-094d7000 rwxp 094b6000 00:00 0          [heap]
b7876000-b7878000 rwxp b7876000 00:00 0 
b7878000-b787c000 r-xp 00000000 08:01 7528479    /usr/lib/libXdmcp.so.6.0.0
b787c000-b787d000 rwxp 00003000 08:01 7528479    /usr/lib/libXdmcp.so.6.0.0
b787d000-b787e000 rwxp b787d000 00:00 0 
b787e000-b7880000 r-xp 00000000 08:01 7528468    /usr/lib/libXau.so.6.0.0
b7880000-b7881000 r-xp 00001000 08:01 7528468    /usr/lib/libXau.so.6.0.0
b7881000-b7882000 rwxp 00002000 08:01 7528468    /usr/lib/libXau.so.6.0.0
b7882000-b789a000 r-xp 00000000 08:01 7544948    /usr/lib/libxcb.so.1.1.0
b789a000-b789b000 r-xp 00017000 08:01 7544948    /usr/lib/libxcb.so.1.1.0
b789b000-b789c000 rwxp 00018000 08:01 7544948    /usr/lib/libxcb.so.1.1.0
b789c000-b78a3000 r-xp 00000000 08:01 4498682    /lib/tls/i686/cmov/librt-2.9.so
b78a3000-b78a4000 r-xp 00006000 08:01 4498682    /lib/tls/i686/cmov/librt-2.9.so
b78a4000-b78a5000 rwxp 00007000 08:01 4498682    /lib/tls/i686/cmov/librt-2.9.so
b78a5000-b78ad000 r-xp 00000000 08:01 7528679    /usr/lib/libdrm.so.2.4.0
b78ad000-b78ae000 r-xp 00007000 08:01 7528679    /usr/lib/libdrm.so.2.4.0
b78ae000-b78af000 rwxp 00008000 08:01 7528679    /usr/lib/libdrm.so.2.4.0
b78af000-b78b3000 r-xp 00000000 08:01 7528483    /usr/lib/libXfixes.so.3.1.0
b78b3000-b78b4000 rwxp 00003000 08:01 7528483    /usr/lib/libXfixes.so.3.1.0
b78b4000-b78b5000 rwxp b78b4000 00:00 0 
b78b5000-b78b7000 r-xp 00000000 08:01 7528477    /usr/lib/libXdamage.so.1.1.0
b78b7000-b78b8000 rwxp 00001000 08:01 7528477    /usr/lib/libXdamage.so.1.1.0
b78b8000-b78bc000 r-xp 00000000 08:01 7528521    /usr/lib/libXxf86vm.so.1.0.0
b78bc000-b78bd000 r-xp 00003000 08:01 7528521    /usr/lib/libXxf86vm.so.1.0.0
b78bd000-b78be000 rwxp 00004000 08:01 7528521    /usr/lib/libXxf86vm.so.1.0.0
b78be000-b78cc000 r-xp 00000000 08:01 7528481    /usr/lib/libXext.so.6.4.0
b78cc000-b78cd000 r-xp 0000d000 08:01 7528481    /usr/lib/libXext.so.6.4.0
b78cd000-b78ce000 rwxp 0000e000 08:01 7528481    /usr/lib/libXext.so.6.4.0
b78ce000-b79b8000 r-xp 00000000 08:01 7528462    /usr/lib/libX11.so.6.2.0
b79b8000-b79b9000 ---p 000ea000 08:01 7528462    /usr/lib/libX11.so.6.2.0
b79b9000-b79ba000 r-xp 000ea000 08:01 7528462    /usr/lib/libX11.so.6.2.0
b79ba000-b79bc000 rwxp 000eb000 08:01 7528462    /usr/lib/libX11.so.6.2.0
b79bc000-b79bd000 rwxp b79bc000 00:00 0 
b79bd000-b79d0000 r-xp 00000000 08:01 7528665    /usr/lib/libdirect-1.0.so.0.1.0
b79d0000-b79d1000 r-xp 00012000 08:01 7528665    /usr/lib/libdirect-1.0.so.0.1.0
b79d1000-b79d2000 rwxp 00013000 08:01 7528665    /usr/lib/libdirect-1.0.so.0.1.0
b79d2000-b79d3000 rwxp b79d2000 00:00 0 
b79d3000-b79da000 r-xp 00000000 08:01 7528747    /usr/lib/libfusion-1.0.so.0.1.0
b79da000-b79db000 r-xp 00006000 08:01 7528747    /usr/lib/libfusion-1.0.so.0.1.0
b79db000-b79dc000 rwxp 00007000 08:01 7528747    /usr/lib/libfusion-1.0.so.0.1.0
b79dc000-b7a40000 r-xp 00000000 08:01 7528667    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a40000-b7a41000 r-xp 00063000 08:01 7528667    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a41000-b7a42000 rwxp 00064000 08:01 7528667    /usr/lib/libdirectfb-1.0.so.0.1.0
b7a42000-b7a44000 r-xp 00000000 08:01 4498658    /lib/tls/i686/cmov/libdl-2.9.so
b7a44000-b7a45000 r-xp 00001000 08:01 4498658    /lib/tls/i686/cmov/libdl-2.9.so
b7a45000-b7a46000 rwxp 00002000 08:01 4498658    /lib/tls/i686/cmov/libdl-2.9.so
b7a46000-b7b09000 r-xp 00000000 08:01 7528542    /usr/lib/libasound.so.2.0.0
b7b09000-b7b0b000 r-xp 000c2000 08:01 7528542    /usr/lib/libasound.so.2.0.0
b7b0b000-b7b0e000 rwxp 000c4000 08:01 7528542    /usr/lib/libasound.so.2.0.0
b7b0e000-b7c6a000 r-xp 00000000 08:01 4498652    /lib/tls/i686/cmov/libc-2.9.so
b7c6a000-b7c6b000 ---p 0015c000 08:01 4498652    /lib/tls/i686/cmov/libc-2.9.so
b7c6b000-b7c6d000 r-xp 0015c000 08:01 4498652    /lib/tls/i686/cmov/libc-2.9.so
b7c6d000-b7c6e000 rwxp 0015e000 08:01 4498652    /lib/tls/i686/cmov/libc-2.9.so
b7c6e000-b7c72000 rwxp b7c6e000 00:00 0 
b7c72000-b7c7f000 r-xp 00000000 08:01 4481089    /lib/libgcc_s.so.1
b7c7f000-b7c80000 r-xp 0000c000 08:01 4481089    /lib/libgcc_s.so.1
b7c80000-b7c81000 rwxp 0000d000 08:01 4481089    /lib/libgcc_s.so.1
b7c81000-b7ca5000 r-xp 00000000 08:01 4498660    /lib/tls/i686/cmov/libm-2.9.so
b7ca5000-b7ca6000 r-xp 00023000 08:01 4498660    /lib/tls/i686/cmov/libm-2.9.so
b7ca6000-b7ca7000 rwxp 00024000 08:01 4498660    /lib/tls/i686/cmov/libm-2.9.so
b7ca7000-b7d8b000 r-xp 00000000 08:01 7544865    /usr/lib/libstdc++.so.6.0.10
b7d8b000-b7d8f000 r-xp 000e3000 08:01 7544865    /usr/lib/libstdc++.so.6.0.10
b7d8f000-b7d90000 rwxp 000e7000 08:01 7544865    /usr/lib/libstdc++.so.6.0.10
b7d90000-b7d96000 rwxp b7d90000 00:00 0 
b7d96000-b7dee000 r-xp 00000000 08:01 8881662    /usr/lib/libGL.so.1.2
b7dee000-b7df3000 r-xp 00057000 08:01 8881662    /usr/lib/libGL.so.1.2
b7df3000-b7df8000 rwxp 0005c000 08:01 8881662    /usr/lib/libGL.so.1.2
b7df8000-b7df9000 rwxp b7df8000 00:00 0 
b7df9000-b7e1d000 r-xp 00000000 08:01 7529223    /usr/lib/libpng12.so.0.27.0
b7e1d000-b7e1e000 r-xp 00023000 08:01 7529223    /usr/lib/libpng12.so.0.27.0
b7e1e000-b7e1f000 rwxp 00024000 08:01 7529223    /usr/lib/libpng12.so.0.27.0
b7e1f000-b7e34000 r-xp 00000000 08:01 4498678    /lib/tls/i686/cmov/libpthread-2.9.so
b7e34000-b7e35000 r-xp 00014000 08:01 4498678    /lib/tls/i686/cmov/libpthread-2.9.so
b7e35000-b7e36000 rwxp 00015000 08:01 4498678    /lib/tls/i686/cmov/libpthread-2.9.so
b7e36000-b7e39000 rwxp b7e36000 00:00 0 
b7e39000-b7ea0000 r-xp 00000000 08:01 7528458    /usr/lib/libSDL-1.2.so.0.11.2
b7ea0000-b7ea1000 ---p 00067000 08:01 7528458    /usr/lib/libSDL-1.2.so.0.11.2
b7ea1000-b7ea2000 r-xp 00067000 08:01 7528458    /usr/lib/libSDL-1.2.so.0.11.2
b7ea2000-b7ea3000 rwxp 00068000 08:01 7528458    /usr/lib/libSDL-1.2.so.0.11.2
b7ea3000-b7ece000 rwxp b7ea3000 00:00 0 
b7ece000-b7ee2000 r-xp 00000000 08:01 4481185    /lib/libz.so.1.2.3.3
b7ee2000-b7ee3000 r-xp 00013000 08:01 4481185    /lib/libz.so.1.2.3.3
b7ee3000-b7ee4000 rwxp 00014000 08:01 4481185    /lib/libz.so.1.2.3.3
b7ef0000-b7ef3000 rwxp b7ef0000 00:00 0 
b7ef3000-b7ef4000 r-xp b7ef3000 00:00 0          [vdso]
b7ef4000-b7f10000 r-xp 00000000 08:01 4481047    /lib/ld-2.9.so
b7f10000-b7f11000 r-xp 0001b000 08:01 4481047    /lib/ld-2.9.so
b7f11000-b7f12000 rwxp 0001c000 08:01 4481047    /lib/ld-2.9.so
bf7fc000-bf811000 rwxp bffeb000 00:00 0          [stack]
Aborted

I pray that this excerpt of computer cuss did not offend anyone, but repeating it seemed a necessary evil. Any advice? Thanks in advance!

---

