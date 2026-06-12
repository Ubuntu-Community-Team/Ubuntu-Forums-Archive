---
title: "Kompozer wont open after installation :("
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Wanas on 2009-04-14
I was looking for a linux free alternative for microsoft front page and I found kompozer.
I installed it through synaptic manager and then I tried to type kompozer in the terminal but I found this message

```
wanas@192:~$ kompozer
*** buffer overflow detected ***: /usr/lib/kompozer/kompozer-bin terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7404da8]
/lib/tls/i686/cmov/libc.so.6[0xb7402eb0]
/lib/tls/i686/cmov/libc.so.6[0xb7403618]
/usr/lib/kompozer/kompozer-bin[0x804e968]
/usr/lib/kompozer/kompozer-bin[0x804ba43]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb731d775]
/usr/lib/kompozer/kompozer-bin[0x804b971]
======= Memory map: ========
08048000-08057000 r-xp 00000000 08:07 156406     /usr/lib/kompozer/kompozer-bin
08057000-08058000 r--p 0000f000 08:07 156406     /usr/lib/kompozer/kompozer-bin
08058000-08059000 rw-p 00010000 08:07 156406     /usr/lib/kompozer/kompozer-bin
08059000-0805a000 rw-p 08059000 00:00 0 
09d30000-09d51000 rw-p 09d30000 00:00 0          [heap]
b7106000-b7109000 rw-p b7106000 00:00 0 
b7109000-b710d000 r-xp 00000000 08:07 9378       /usr/lib/libXdmcp.so.6.0.0
b710d000-b710e000 rw-p 00003000 08:07 9378       /usr/lib/libXdmcp.so.6.0.0
b710e000-b710f000 rw-p b710e000 00:00 0 
b710f000-b7111000 r-xp 00000000 08:07 9367       /usr/lib/libXau.so.6.0.0
b7111000-b7112000 r--p 00001000 08:07 9367       /usr/lib/libXau.so.6.0.0
b7112000-b7113000 rw-p 00002000 08:07 9367       /usr/lib/libXau.so.6.0.0
b7113000-b7137000 r-xp 00000000 08:07 9629       /usr/lib/libexpat.so.1.5.2
b7137000-b7139000 r--p 00023000 08:07 9629       /usr/lib/libexpat.so.1.5.2
b7139000-b713a000 rw-p 00025000 08:07 9629       /usr/lib/libexpat.so.1.5.2
b713a000-b7152000 r-xp 00000000 08:07 10342      /usr/lib/libxcb.so.1.1.0
b7152000-b7153000 r--p 00017000 08:07 10342      /usr/lib/libxcb.so.1.1.0
b7153000-b7154000 rw-p 00018000 08:07 10342      /usr/lib/libxcb.so.1.1.0
b7154000-b715a000 r-xp 00000000 08:07 10340      /usr/lib/libxcb-render.so.0.0.0
b715a000-b715b000 r--p 00005000 08:07 10340      /usr/lib/libxcb-render.so.0.0.0
b715b000-b715c000 rw-p 00006000 08:07 10340      /usr/lib/libxcb-render.so.0.0.0
b715c000-b715f000 r-xp 00000000 08:07 10338      /usr/lib/libxcb-render-util.so.0.0.0
b715f000-b7160000 r--p 00002000 08:07 10338      /usr/lib/libxcb-render-util.so.0.0.0
b7160000-b7161000 rw-p 00003000 08:07 10338      /usr/lib/libxcb-render-util.so.0.0.0
b7161000-b7162000 rw-p b7161000 00:00 0 
b7162000-b7186000 r-xp 00000000 08:07 10129      /usr/lib/libpng12.so.0.27.0
b7186000-b7187000 r--p 00023000 08:07 10129      /usr/lib/libpng12.so.0.27.0
b7187000-b7188000 rw-p 00024000 08:07 10129      /usr/lib/libpng12.so.0.27.0
b7188000-b719b000 r-xp 00000000 08:07 9567       /usr/lib/libdirect-1.0.so.0.1.0
b719b000-b719c000 r--p 00012000 08:07 9567       /usr/lib/libdirect-1.0.so.0.1.0
b719c000-b719d000 rw-p 00013000 08:07 9567       /usr/lib/libdirect-1.0.so.0.1.0
b719d000-b71a4000 r-xp 00000000 08:07 9651       /usr/lib/libfusion-1.0.so.0.1.0
b71a4000-b71a5000 r--p 00006000 08:07 9651       /usr/lib/libfusion-1.0.so.0.1.0
b71a5000-b71a6000 rw-p 00007000 08:07 9651       /usr/lib/libfusion-1.0.so.0.1.0
b71a6000-b720a000 r-xp 00000000 08:07 9569       /usr/lib/libdirectfb-1.0.so.0.1.0
b720a000-b720b000 r--p 00063000 08:07 9569       /usr/lib/libdirectfb-1.0.so.0.1.0
b720b000-b720c000 rw-p 00064000 08:07 9569       /usr/lib/libdirectfb-1.0.so.0.1.0
b720c000-b724c000 r-xp 00000000 08:07 10123      /usr/lib/libpixman-1.so.0.13.2
b724c000-b724e000 r--p 0003f000 08:07 10123      /usr/lib/libpixman-1.so.0.13.2
b724e000-b724f000 rw-p 00041000 08:07 10123      /usr/lib/libpixman-1.so.0.13.2
b724f000-b7250000 rw-p b724f000 00:00 0 
b7250000-b7268000 r-xp 00000000 08:07 2665       /lib/libselinux.so.1
b7268000-b7269000 r--p 00017000 08:07 2665       /lib/libselinux.so.1
b7269000-b726a000 rw-p 00018000 08:07 2665       /lib/libselinux.so.1
b726a000-b729a000 r-xp 00000000 08:07 2651       /lib/libpcre.so.3.12.1
b729a000-b729b000 r--p 0002f000 08:07 2651       /lib/libpcre.so.3.12.1
b729b000-b729c000 rw-p 00030000 08:07 2651       /lib/libpcre.so.3.12.1
b729c000-b72b0000 r-xp 00000000 08:07 2696       /lib/libz.so.1.2.3.3
b72b0000-b72b1000 r--p 00013000 08:07 2696       /lib/libz.so.1.2.3.3
b72b1000-b72b2000 rw-p 00014000 08:07 2696       /lib/libz.so.1.2.3.3
b72b2000-b72ba000 r-xp 00000000 08:07 9374       /usr/lib/libXcursor.so.1.0.2
b72ba000-b72bb000 rw-p 00007000 08:07 9374       /usr/lib/libXcursor.so.1.0.2
b72bb000-b72c1000 r-xp 00000000 08:07 9400       /usr/lib/libXrandr.so.2.2.0
b72c1000-b72c2000 r--p 00006000 08:07 9400       /usr/lib/libXrandr.so.2.2.0
b72c2000-b72c3000 rw-p 00007000 08:07 9400       /usr/lib/libXrandr.so.2.2.0
b72c3000-b72c4000 rw-p b72c3000 00:00 0 
b72c4000-b72cc000 r-xp 00000000 08:07 9388       /usr/lib/libXi.so.6.0.0
b72cc000-b72cd000 r--p 00007000 08:07 9388       /usr/lib/libXi.so.6.0.0
b72cd000-b72ce000 rw-p 00008000 08:07 9388       /usr/lib/libXi.so.6.0.0
b72ce000-b72d0000 r-xp 00000000 08:07 9390       /usr/lib/libXinerama.so.1.0.0
b72d0000-b72d1000 rw-p 00001000 08:07 9390       /usr/lib/libXinerama.so.1.0.0
b72d1000-b72d9000 r-xp 00000000 08:07 9402       /usr/lib/libXrender.so.1.3.0
b72d9000-b72da000 r--p 00007000 08:07 9402       /usr/lib/libXrender.so.1.3.0
b72da000-b72db000 rw-p 00008000 08:07 9402       /usr/lib/libXrender.so.1.3.0
b72db000-b72e9000 r-xp 00000000 08:07 9380       /usr/lib/libXext.so.6.4.0
b72e9000-b72ea000 r--p 0000d000 08:07 9380       /usr/lib/libXext.so.6.4.0
b72ea000-b72eb000 rw-p 0000e000 08:07 9380       /usr/lib/libXext.so.6.4.0
b72eb000-b72ef000 r-xp 00000000 08:07 9382       /usr/lib/libXfixes.so.3.1.0
b72ef000-b72f0000 rw-p 00003000 08:07 9382       /usr/lib/libXfixes.so.3.1.0
b72f0000-b72f1000 rw-p b72f0000 00:00 0 
b72f1000-b72f3000 r-xp 00000000 08:07 9376       /usr/lib/libXdamage.so.1.1.0
b72f3000-b72f4000 rw-p 00001000 08:07 9376       /usr/lib/libXdamage.so.1.1.0
b72f4000-b72f6000 r-xp 00000000 08:07 9372       /usr/lib/libXcomposite.so.1.0.0
b72f6000-b72f7000 r--p 00001000 08:07 9372       /usr/lib/libXcomposite.so.1.0.0
b72f7000-b72f8000 rw-p 00002000 08:07 9372       /usr/lib/libXcomposite.so.1.0.0
b72f8000-b7305000 r-xp 00000000 08:07 2601       /lib/libgcc_s.so.1
b7305000-b7306000 r--p 0000c000 08:07 2601       /lib/libgcc_s.so.1
b7306000-b7307000 rw-p 0000d000 08:07 2601       /lib/libgcc_s.so.1
b7307000-b7463000 r-xp 00000000 08:07 6169       /lib/tls/i686/cmov/libc-2.9.so
b7463000-b7464000 ---p 0015c000 08:07 6169       /lib/tls/i686/cmov/libc-2.9.so
b7464000-b7466000 r--p 0015c000 08:07 6169       /lib/tls/i686/cmov/libc-2.9.so
b7466000-b7467000 rw-p 0015e000 08:07 6169       /lib/tls/i686/cmov/libc-2.9.so
b7467000-b746a000 rw-p b7467000 00:00 0 
b746a000-b754e000 r-xp 00000000 08:07 10259      /usr/lib/libstdc++.so.6.0.10
b754e000-b7552000 r--p 000e3000 08:07 10259      /usr/lib/libstdc++.so.6.0.10
b7552000-b7553000 rw-p 000e7000 08:07 10259      /usr/lib/libstdc++.so.6.0.10
b7553000-b7559000 rw-p b7553000 00:00 0 
b7559000-b757d000 r-xp 00000000 08:07 6177       /lib/tls/i686/cmov/libm-2.9.so
b757d000-b757e000 r--p 00023000 08:07 6177       /lib/tls/i686/cmov/libm-2.9.so
b757e000-b757f000 rw-p 00024000 08:07 6177       /lib/tls/i686/cmov/libm-2.9.so
b757f000-b7580000 rw-p b757f000 00:00 0 
b7580000-b766a000 r-xp 00000000 08:07 9361       /usr/lib/libX11.so.6.2.0
b766a000-b766b000 ---p 000ea000 08:07 9361       /usr/lib/libX11.so.6.2.0
b766b000-b766c000 r--p 000ea000 08:07 9361       /usr/lib/libX11.so.6.2.0
b766c000-b766e000 rw-p 000eb000 08:07 9361       /usr/lib/libX11.so.6.2.0
b766e000-b766f000 rw-p b766e000 00:00 0 
b766f000-b7724000 r-xp 00000000 08:07 9728       /usr/lib/libglib-2.0.so.0.2000.0
b7724000-b7725000 r--p 000b5000 08:07 9728       /usr/lib/libglib-2.0.so.0.2000.0
b7725000-b7726000 rw-p 000b6000 08:07 9728       /usr/lib/libglib-2.0.so.0.2000.0
b7726000-b7729000 r-xp 00000000 08:07 9740       /usr/lib/libgmodule-2.0.so.0.2000.0
b7729000-b772a000 r--p 00002000 08:07 9740       /usr/lib/libgmodule-2.0.so.0.2000.0
b772a000-b772b000 rw-p 00003000 08:07 9740       /usr/lib/libgmodule-2.0.so.0.2000.0
b772b000-b7767000 r-xp 00000000 08:07 9782       /usr/lib/libgobject-2.0.so.0.2000.0
b7767000-b7768000 r--p 0003b000 08:07 9782       /usr/lib/libgobject-2.0.so.0.2000.0
b7768000-b7769000 rw-p 0003c000 08:07 9782       /usr/lib/libgobject-2.0.so.0.2000.0
b7769000-b7794000 r-xp 00000000 08:07 9639       /usr/lib/libfontconfig.so.1.3.0
b7794000-b7795000 r--p 0002a000 08:07 9639       /usr/lib/libfontconfig.so.1.3.0
b7795000-b7796000 rw-p 0002b000 08:07 9639       /usr/lib/libfontconfig.so.1.3.0
b7796000-b7797000 rw-p b7796000 00:00 0 
b7797000-b7809000 r-xp 00000000 08:07 9647       /usr/lib/libfreetype.so.6.3.20
b7809000-b780d000 r--p 00071000 0Aborted (core dumped)
```

---

### Post by dje on 2009-04-14
are you using jaunty? if so you are experiencing [bug 347779]("http://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/347779")

dje

---

### Post by Wanas on 2009-04-14
Sorry for not posting my ubuntu release 
yeah I am using ubuntu jaunty 

I want to ask another question how to search for bugs for ubuntu, to know is this is a known bug or its only an error for me

---

### Post by dje on 2009-04-14
no worries, just remember that in future it helps to include which release you are using :)

you can browse bugs at [http://bugs.launchpad.net/ubuntu](http://bugs.launchpad.net/ubuntu)

you may wish to try quanta as a replacement for kompozer:
```
sudo apt-get install quanta
```

dje

---

### Post by Wanas on 2009-04-14
yeah thanks dje 
I will give it a try 
and about the kompzer I downloaded the alpha release from [here]("http://sourceforge.net/project/showfiles.php?group_id=170132&package_id=194013&release_id=673725") and it works cool but I will try quanta too to see which is easier ;)

---

