---
title: "X Server restart on VT switch - Asus EEE"
date: 2009-04-01
forum: Hardware
---

### Post by C.E. Shannon on 2009-04-01
I recently installed 8.04 LTS on an EEE Box B202.  X opens fine, but when I switch to F2, etc it will automatically restart after a minute, making it impossible to work from the command line.  

Any help will be appreciated!

Thanks,
Matt

I will attach xorg.conf

lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)


Backtrace:

(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 3

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7fa4420]
2: /usr/X11R6/bin/X [0x80d86bc]
3: /usr/lib/xorg/modules/extensions//libextmod.so(XvdiSetPortAttribute+0x4e) [0xb7c1d9ee]
4: /usr/lib/xorg/modules/extensions//libextmod.so [0xb7c20c5c]
5: /usr/X11R6/bin/X [0x81506ee]
6: /usr/X11R6/bin/X(Dispatch+0x2cf) [0x808d8df]
7: /usr/X11R6/bin/X(main+0x48b) [0x807471b]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d44450]
9: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

---

