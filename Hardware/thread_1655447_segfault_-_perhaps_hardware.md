---
title: "segfault - perhaps hardware"
date: 2010-12-29
forum: Hardware
---

### Post by gerardc on 2010-12-29
Hi , I am seeing a large amount of segfault errors, can anyone point me to a doc or url that I can strat trying understand what is causing the error's.


Dec 29 16:39:43 gc-linux kernel: [99683.254416] operapluginwrap[17607]: segfault at 0 ip (null) sp bf92bf1c error 4 in libstdc++.so.6.0.13[110000+e9000]
Dec 29 16:39:43 gc-linux kernel: [99683.300673] operapluginwrap[17610]: segfault at 0 ip (null) sp bf8d78cc error 4 in libgcc_s.so.1[110000+1d000]
Dec 29 16:39:44 gc-linux kernel: [99683.693837] operapluginwrap[17615]: segfault at 0 ip (null) sp bfaa479c error 4 in librt-2.11.1.so[110000+7000]
Dec 29 16:52:34 gc-linux kernel: [100453.571597] operapluginwrap[17719]: segfault at 0 ip (null) sp bfdc0b7c error 4 in libdl-2.11.1.so[110000+2000]
Dec 29 16:52:34 gc-linux kernel: [100453.579699] operapluginwrap[17721]: segfault at 0 ip (null) sp bfc1023c error 4 in libX11.so.6.3.0[110000+119000]
Dec 29 16:52:34 gc-linux kernel: [100453.629952] operapluginwrap[17725]: segfault at 0 ip (null) sp bffa1e8c error 4 in libXau.so.6.0.0[110000+2000]
Dec 29 16:52:34 gc-linux kernel: [100454.019422] operapluginwrap[17730]: segfault at 0 ip (null) sp bfac718c error 4 in libc-2.11.1.so[110000+153000]
Dec 29 16:52:34 gc-linux kernel: [100454.027305] operapluginwrap[17731]: segfault at 0 ip (null) sp bfc65cfc error 4 in libX11.so.6.3.0[110000+119000]
Dec 29 16:52:34 gc-linux kernel: [100454.035224] operapluginwrap[17732]: segfault at 0 ip (null) sp bfcaf30c error 4 in libc-2.11.1.so[110000+153000]
Dec 29 16:52:34 gc-linux kernel: [100454.079907] operapluginwrap[17735]: segfault at 0 ip (null) sp bf9442cc error 4 in libX11.so.6.3.0[110000+119000]
Dec 29 16:52:35 gc-linux kernel: [100454.442986] operapluginwrap[17740]: segfault at 0 ip (null) sp bfca0a8c error 4 in libX11.so.6.3.0[110000+119000]
Dec 29 19:39:15 gc-linux kernel: [110454.692814] gvfsd-metadata[2912]: segfault at 8 ip 0804d35a sp bfe71740 error 4 in gvfsd-metadata[8048000+c000]
Dec 29 19:41:21 gc-linux kernel: [110580.645594] gvfsd-metadata[20376]: segfault at 8 ip 0804d35a sp bfdc3560 error 4 in gvfsd-metadata[8048000+c000]
Dec 29 19:49:37 gc-linux kernel: [111076.664559] gvfsd-metadata[20436]: segfault at 8 ip 0804d35a sp bf914b30 error 4 in gvfsd-metadata[8048000+c000]
Dec 29 19:50:52 gc-linux kernel: [111151.646406] gvfsd-metadata[20542]: segfault at 8 ip 0804d35a sp bf82ba60 error 4 in gvfsd-metadata[8048000+c000]
Dec 29 19:52:04 gc-linux kernel: [111223.693266] gvfsd-metadata[20607]: segfault at 8 ip 0804d35a sp bfcdab10 error 4 in gvfsd-metadata[8048000+c000]
Dec 29 19:53:19 gc-linux kernel: [111298.698863] gvfsd-metadata[20671]: segfault at 8 ip 0804d35a sp bff58b20 error 4 in gvfsd-metadata[8048000+c000]
Dec 29 19:54:52 gc-linux kernel: [111391.616474] operapluginwrap[20695]: segfault at 0 ip (null) sp bfc1116c error 4 in libXext.so.6.4.0[110000+e000]
Dec 29 19:54:52 gc-linux kernel: [111391.624414] operapluginwrap[20696]: segfault at 0 ip (null) sp bfc5dddc error 4 in libuuid.so.1.3.0[110000+3000]
Dec 29 19:54:52 gc-linux kernel: [111391.673969] operapluginwrap[20701]: segfault at 0 ip (null) sp bfe0e5cc error 4 in libXext.so.6.4.0[110000+e000]
Dec 29 19:54:52 gc-linux kernel: [111392.066377] operapluginwrap[20707]: segfault at 0 ip (null) sp bfaba6cc error 4 in libXext.so.6.4.0[110000+e000]
Dec 29 19:54:52 gc-linux kernel: [111392.074443] operapluginwrap[20708]: segfault at 0 ip (null) sp bfdcb17c error 4 in libICE.so.6.3.0[110000+15000]
Dec 29 19:54:52 gc-linux kernel: [111392.082407] operapluginwrap[20709]: segfault at 0 ip (null) sp bff9321c error 4 in libSM.so.6.0.1[110000+7000]
Dec 29 19:54:52 gc-linux kernel: [111392.126995] operapluginwrap[20712]: segfault at 0 ip (null) sp bfe7c41c error 4 in libstdc++.so.6.0.13[110000+e9000]
Dec 29 19:54:53 gc-linux kernel: [111392.510275] operapluginwrap[20717]: segfault at 0 ip (null) sp bf83f06c error 4 in libXt.so.6.0.0[110000+4f000]
Dec 29 20:02:26 gc-linux kernel: [111846.348482] chrome[20851]: segfault at 94b11b68 ip 08b60677 sp bfd06000 error 4 in chrome[8048000+29d3000]


Ubuntu 10.04, is it perhaps a HDD failure ?.

Thanks

---

