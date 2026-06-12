---
title: "Privoxy crashing with glibc errors since Hardy upgrade"
date: 2008-07-18
forum: General Help
---

### Post by Polverone on 2008-07-18
I successfully installed and used Tor and Privoxy under 7.04 and it continued to work under 7.10. I used Privoxy heavily for 9 months with no trouble. Since I've upgraded to 8.04 (now 8.04.1), Privoxy has regularly crashed for me. I only discovered what was happening when I forced it to run in non-daemon mode in a terminal, since it died without leaving log messages.

Here's a typical example of the crash output:
```

Jul 18 10:31:42.671 Privoxy(b7df96b0) Info: Privoxy version 3.0.8
Jul 18 10:31:42.671 Privoxy(b7df96b0) Info: Program name: privoxy
*** glibc detected *** privoxy: double free or corruption (!prev): 0x080d9b98 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e65a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e694f0]
privoxy[0x806c50c]
privoxy[0x8067608]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7e10450]
privoxy[0x8049ca1]
======= Memory map: ========
08048000-08080000 r-xp 00000000 08:01 3671896    /usr/sbin/privoxy
08080000-08081000 rw-p 00038000 08:01 3671896    /usr/sbin/privoxy
08081000-080e1000 rw-p 08081000 00:00 0          [heap]
b7400000-b7421000 rw-p b7400000 00:00 0 
b7421000-b7500000 ---p b7421000 00:00 0 
b75e2000-b75ec000 r-xp 00000000 08:01 278614     /lib/libgcc_s.so.1
b75ec000-b75ed000 rw-p 0000a000 08:01 278614     /lib/libgcc_s.so.1
b75ed000-b75ee000 ---p b75ed000 00:00 0 
b75ee000-b7dee000 rw-p b75ee000 00:00 0 
b7dee000-b7df7000 r-xp 00000000 08:01 1179745    /lib/tls/i686/cmov/libnss_files-2.7.so
b7df7000-b7df9000 rw-p 00008000 08:01 1179745    /lib/tls/i686/cmov/libnss_files-2.7.so
b7df9000-b7dfa000 rw-p b7df9000 00:00 0 
b7dfa000-b7f43000 r-xp 00000000 08:01 1179731    /lib/tls/i686/cmov/libc-2.7.so
b7f43000-b7f44000 r--p 00149000 08:01 1179731    /lib/tls/i686/cmov/libc-2.7.so
b7f44000-b7f46000 rw-p 0014a000 08:01 1179731    /lib/tls/i686/cmov/libc-2.7.so
b7f46000-b7f49000 rw-p b7f46000 00:00 0 
b7f49000-b7f5d000 r-xp 00000000 08:01 1179750    /lib/tls/i686/cmov/libpthread-2.7.so
b7f5d000-b7f5f000 rw-p 00013000 08:01 1179750    /lib/tls/i686/cmov/libpthread-2.7.so
b7f5f000-b7f61000 rw-p b7f5f000 00:00 0 
b7f61000-b7f62000 r-xp 00000000 08:01 410369     /usr/lib/libpcreposix.so.3.12.1
b7f62000-b7f63000 rw-p 00000000 08:01 410369     /usr/lib/libpcreposix.so.3.12.1
b7f63000-b7f64000 rw-p b7f63000 00:00 0 
b7f64000-b7f8a000 r-xp 00000000 08:01 410368     /usr/lib/libpcre.so.3.12.1
b7f8a000-b7f8b000 rw-p 00026000 08:01 410368     /usr/lib/libpcre.so.3.12.1
b7f8b000-b7f9f000 r-xp 00000000 08:01 311715     /usr/lib/libz.so.1.2.3.3
b7f9f000-b7fa0000 rw-p 00013000 08:01 311715     /usr/lib/libz.so.1.2.3.3
b7fb4000-b7fb6000 rw-p b7fb4000 00:00 0 
b7fb6000-b7fb7000 r-xp b7fb6000 00:00 0          [vdso]
b7fb7000-b7fd1000 r-xp 00000000 08:01 278737     /lib/ld-2.7.so
b7fd1000-b7fd3000 rw-p 00019000 08:01 278737     /lib/ld-2.7.so
bfe30000-bfe45000 rw-p bffeb000 00:00 0          [stack]
Aborted

```

I've tried uninstalling and re-installing Privoxy and Tor both to no avail. When Privoxy is in use it crashes at unpredictable intervals, usually about 15 minutes apart. I've wrapped Privoxy in an automatic restart script so I can use it in the mean time, but I'd like to fix the underlying problem. I haven't had any other problems since my Hardy upgrade. This is a Core 2 Duo laptop running in 32 bit mode.

---

