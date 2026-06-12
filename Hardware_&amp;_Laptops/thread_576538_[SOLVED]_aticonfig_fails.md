---
title: "[SOLVED] aticonfig fails"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by GhentK on 2007-10-15
Hi all,

I have a problem with aticonfig and xorg.conf. Whenever I try to use aticonfig to alter xorg.conf -- for instance the second monitor -- it outputs the following:

```
user@user:~$ sudo aticonfig --desktop-setup=single
Warning: Option 'DesktopSetup' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbf96c9c1 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7ccf92b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7c78050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:01 2692966    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:01 2692966    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7c54000-b7c55000 rw-p b7c54000 00:00 0 
b7c55000-b7c57000 r-xp 00000000 08:01 3894025    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c57000-b7c59000 rw-p 00001000 08:01 3894025    /lib/tls/i686/cmov/libdl-2.6.1.so
b7c59000-b7c5a000 rw-p b7c59000 00:00 0 
b7c5a000-b7c5e000 r-xp 00000000 08:01 2693844    /usr/lib/libXdmcp.so.6.0.0
b7c5e000-b7c5f000 rw-p 00003000 08:01 2693844    /usr/lib/libXdmcp.so.6.0.0
b7c5f000-b7c61000 r-xp 00000000 08:01 2693833    /usr/lib/libXau.so.6.0.0
b7c61000-b7c62000 rw-p 00001000 08:01 2693833    /usr/lib/libXau.so.6.0.0
b7c62000-b7da6000 r-xp 00000000 08:01 3894019    /lib/tls/i686/cmov/libc-2.6.1.so
b7da6000-b7da7000 r--p 00143000 08:01 3894019    /lib/tls/i686/cmov/libc-2.6.1.so
b7da7000-b7da9000 rw-p 00144000 08:01 3894019    /lib/tls/i686/cmov/libc-2.6.1.so
b7da9000-b7dac000 rw-p b7da9000 00:00 0 
b7dac000-b7dcf000 r-xp 00000000 08:01 3894027    /lib/tls/i686/cmov/libm-2.6.1.so
b7dcf000-b7dd1000 rw-p 00023000 08:01 3894027    /lib/tls/i686/cmov/libm-2.6.1.so
b7dd1000-b7ebe000 r-xp 00000000 08:01 2693827    /usr/lib/libX11.so.6.2.0
b7ebe000-b7ec2000 rw-p 000ed000 08:01 2693827    /usr/lib/libX11.so.6.2.0
b7ec2000-b7ecf000 r-xp 00000000 08:01 2693848    /usr/lib/libXext.so.6.4.0
b7ecf000-b7ed0000 rw-p 0000d000 08:01 2693848    /usr/lib/libXext.so.6.4.0
b7ed0000-b7ed1000 rw-p b7ed0000 00:00 0 
b7ed1000-b7ed8000 r-xp 00000000 08:01 2693870    /usr/lib/libXrender.so.1.3.0
b7ed8000-b7ed9000 rw-p 00006000 08:01 2693870    /usr/lib/libXrender.so.1.3.0
b7ed9000-b7ede000 r-xp 00000000 08:01 2693868    /usr/lib/libXrandr.so.2.1.0
b7ede000-b7edf000 rw-p 00005000 08:01 2693868    /usr/lib/libXrandr.so.2.1.0
b7edf000-b7ee9000 r-xp 00000000 08:01 3890659    /lib/libgcc_s.so.1
b7ee9000-b7eea000 rw-p 0000a000 08:01 3890659    /lib/libgcc_s.so.1
b7eea000-b7eed000 rw-p b7eea000 00:00 0 
b7eed000-b7f07000 r-xp 00000000 08:01 3890612    /lib/ld-2.6.1.so
b7f07000-b7f09000 rw-p 00019000 08:01 3890612    /lib/ld-2.6.1.so
bf958000-bf96e000 rw-p bf958000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
```

I'm on Ubuntu 7.10 RC, and it worked on the first day of install. Does it have anything to do with the fact that I have visual effects switched on (and therfore xserver-xgl installed)?

---

### Post by rcmn on 2007-10-17
exact same problem here .Did you find a solution ?
i have a ati radeon 9800 pro.

---

### Post by GhentK on 2007-10-18
Nope, I haven't. I'll try uninstalling the xgl package now. I'll return with results.

---

### Post by GhentK on 2007-10-18
It's simply because xorg.conf is being used by eye-candy software (I feel so stupid now; I should've just looked at the error output!). apt-get remove xserver-xgl in order to change xorg.conf with aticonfig... or edit it manually. ;)

Solved.

---

