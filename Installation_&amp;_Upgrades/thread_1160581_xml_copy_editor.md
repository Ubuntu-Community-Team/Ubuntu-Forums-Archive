---
title: "xml copy editor"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by cferreira on 2009-05-15
When I run Ubuntu 8.04 hardy XML Copy Editor was working nice. Then, after a regular update, the software crashs continuously.
Now that I upgrade to Ubuntu Jaunty I keep getting the following error.

I have installed xmlcopyeditor using dpkg -i  xmlcopyeditor1.2.0.4.deb.

[URL="http://ubuntuforums.org/register.php?a=act&u=836101&i=f335bc5a24e875e3a9251682088f1cd116f26729"][FONT=Verdana]$ xmlcopyeditor 
*** glibc detected *** xmlcopyeditor: double free or corruption (out): 0x093e4770 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6ca1604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb6ca35b6]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb6e9c231]
xmlcopyeditor(_ZN11xercesc_2_813XSerializableD0Ev+0x23)[0x80f9b4d]
/usr/local/lib/libxerces-c.so.28(_ZN11xercesc_2_814RefHashTableOfINS_7GrammarEE9removeAllEv+0x6a)[0xb714a4ea]
/usr/local/lib/libxerces-c.so.28(_ZN11xercesc_2_814RefHashTableOfINS_7GrammarEE7cleanupEv+0x22)[0xb714a562]
/usr/local/lib/libxerces-c.so.28(_ZN11xercesc_2_814RefHashTableOfINS_7GrammarEED1Ev+0x1d)[0xb714a5bd]
/usr/local/lib/libxerces-c.so.28(_ZN11xercesc_2_815GrammarResolverD1Ev+0x2c)[0xb714900c]
/usr/local/lib/libxerces-c.so.28(_ZN11xercesc_2_817AbstractDOMParser7cleanUpEv+0x79)[0xb70a7789]
/usr/local/lib/libxerces-c.so.28(_ZN11xercesc_2_817AbstractDOMParserD2Ev+0x53)[0xb70a8cd3]
/usr/local/lib/libxerces-c.so.28(_ZN11xercesc_2_815XercesDOMParserD0Ev+0x50)[0xb7205520]
xmlcopyeditor[0x80f64e7]
xmlcopyeditor[0x80f8a6e]
/usr/lib/libexpat.so.1[0xb7541beb]
/usr/lib/libexpat.so.1[0xb7542c11]
/usr/lib/libexpat.so.1[0xb75445ef]
/usr/lib/libexpat.so.1[0xb7544ce7]
/usr/lib/libexpat.so.1(XML_ParseBuffer+0x7c)[0xb753b68c]
/usr/lib/libexpat.so.1(XML_Parse+0xd3)[0xb753cb43]
xmlcopyeditor[0x80fea05]
xmlcopyeditor[0x80e58f5]
xmlcopyeditor[0x8082f19]
xmlcopyeditor[0x8083772]
xmlcopyeditor[0x80a5dc4]
xmlcopyeditor[0x80adeee]
xmlcopyeditor(_ZN12wxAppConsole10CallOnInitEv+0x18)[0x80aff76]
/usr/local/lib/libwx_baseu-2.8.so.0(_Z7wxEntryRiPPw+0x40)[0xb75e87b0]
/usr/local/lib/libwx_baseu-2.8.so.0(_Z7wxEntryRiPPc+0x37)[0xb75e8887]
xmlcopyeditor[0x80afa0e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb6c48775]
xmlcopyeditor[0x8064cd1]
======= Memory map: ========
08048000-08150000 r-xp 00000000 08:02 1390176    /usr/local/bin/xmlcopyeditor
08150000-08151000 r--p 00108000 08:02 1390176    /usr/local/bin/xmlcopyeditor
08151000-08153000 rw-p 00109000 08:02 1390176    /usr/local/bin/xmlcopyeditor
08153000-0815a000 rw-p 08153000 00:00 0 
090ad000-09410000 rw-p 090ad000 00:00 0          [heap]
b4f00000-b4f21000 rw-p b4f00000 00:00 0 
b4f21000-b5000000 ---p b4f21000 00:00 0 
b50fa000-b5109000 r--p 00000000 08:02 1488152    /usr/share/fonts/truetype/ttf-bitstream-vera/VeraBd.ttf
b5109000-b511a000 r--p 00000000 08:02 1488150    /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf
b511a000-b51a6000 r--p 00000000 08:02 1913787    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b51a6000-b523e000 r--p 00000000 08:02 1488072    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b523e000-b524d000 r-xp 00000000 08:02 1242776    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b524d000-b524e000 r--p 0000e000 08:02 1242776    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b524e000-b524f000 rw-p 0000f000 08:02 1242776    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b524f000-b5285000 r-xp 00000000 08:02 5102623    /lib/libdbus-1.so.3.4.0
b5285000-b5286000 r--p 00035000 08:02 5102623    /lib/libdbus-1.so.3.4.0
b5286000-b5287000 rw-p 00036000 08:02 5102623    /lib/libdbus-1.so.3.4.0
b528d000-b528f000 r-xp 00000000 08:02 1358120    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b528f000-b5290000 r--p 00001000 08:02 1358120    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5290000-b5291000 rw-p 00002000 08:02 1358120    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5291000-b5294000 r--s 00000000 08:02 2784585    /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b5294000-b529a000 r--s 00000000 08:02 3795466    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b529a000-b529d000 r--s 00000000 08:02 2784523    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b529d000-b529e000 r--s 00000000 08:02 2784454    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b529e000-b52a0000 r--s 00000000 08:02 2784562    /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b52a0000-b52a1000 r--s 00000000 08:02 2784530    /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b52a1000-b52a2000 r--s 00000000 08:02 2784547    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b52a2000-b52a6000 r--s 00000000 08:02 2784537    /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b52a6000-b52a8000 r--s 00000000 08:02 2784379    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b52a8000-b52ab000 r--s 00000000 08:02 2787666    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b52ab000-b52ac000 r--s 00000000 08:02 2784514    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b52ac000-b52ae000 r--s 00000000 08:02 2784573    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b52ae000-b52b1000 r--s 00000000 08:02 2784430    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b52b1000-b52b3000 r--s 00000000 08:02 2784419    /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b52b3000-b52b6000 r--s 00000000 08:02 2784401    /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b52b6000-b52bd000 r--s 00000000 08:02 2784455    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b52bd000-b52c0000 r--s 00000000 08:02 2784446    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b52c0000-b52c2000 r--s 00000000 08:02 2784385    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b52c2000-b52ca000 r--s 00000000 08:02 2784372    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b52ca000-b52d5000 r--s 00000000 08:02 3795468    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b52d5000-b52d7000 r--s 00000000 08:02 2787658    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b52d7000-b52d8000 r--s 00000000 08:02 2784538    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b52d8000-b52db000 r--s 00000000 08:02 2787644    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b52db000-b52e2000 r--s 00000000 08:02 2784494    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b52e2000-b52e5000 r--s 00000000 08:02 2784536    /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b52e5000-b52ee000 r--s 00000000 08:02 2787645    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b52ee000-b52fb000 r--s 00000000 08:02 2787565    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b52fb000-b5309000 r--s 00000000 08:02 2787564    /var/cache/fontconfig/865f88548240fee46819705c6468c165-x86.cache-2
b5309000-b530f000 r-xp 00000000 08:02 1292066    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b530f000-b5310000 r--p 00005000 08:02 1292066    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5310000-b5311000 rw-p 00006000 08:02 1292066    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5311000-b532b000 r--s 00000000 08:02 1391074    /usr/share/mime/mime.cache
b532b000-b5345000 r-xp 00000000 08:02 1242865    /usr/lib/gio/modules/libgvfsdbus.so
b5345000-b5346000 r--p 00019000 08:02 1242865    /usr/lib/gio/modules/libgvfsdbus.so
b5346000-b5347000 rw-p 0001a000 08:02 1242865    /usr/lib/gio/modules/libgvfsdbus.so
b534a000-b5715000 r--p 00000000 08:02 5315221    /usr/share/icons/hicolor/icon-theme.cache
b5715000-b5d59000 r--p 00000000 08:02 5281766    /usr/share/icons/gnome/icon-theme.cache
b5d59000-b5e04000 r--p 00000000 08:02 1604185    /usr/share/icons/Tangerine/icon-theme.cache
b5e04000-b5f77000 r--p 00000000 08:02 1602515    /usr/share/icons/Human/icon-theme.cache
b5f77000-b5fd7000 rw-s 00000000 00:09 3604502    /SYSV00000000 (deleted)
b5fd7000-b5ff7000 r-xp 00000000 08:02 1291852    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b5ff7000-b5ff8000 r--p 00020000 08:02 1291852    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b5ff8000-b5ff9000 rw-p 00021000 08:02 1291852    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b5ff9000-b6000000 r-xp 00000000 08:02 1226477    /usr/lib/libltdl.so.7.2.0
b6000000-b6001000 r--p 00006000 08:02 1226477    /usr/lib/libltdl.so.7.2.0
b6001000-b6002000 rw-p 00007000 08:02 1226477    /usr/lib/libltdl.so.7.2.0
b6002000-b600e000 r-xp 00000000 08:02 1230229    /usr/lib/libtdb.so.1.1.3
b600e000-b600f000 r--p 0000b000 08:02 1230229    /usr/lib/libtdb.so.1.1.3
b600f000-b6010000 rw-p 0000c000 08:02 1230229    /usr/lib/libtdb.so.1.1.3
b6010000-b6014000 r-xp 00000000 08:02 1227345    /usr/lib/libogg.so.0.5.3
b6014000-b6015000 r--p 00003000 08:02 1227345    /usr/lib/libogg.so.0.5.3
b6015000-b6016000 rw-p 00004000 08:02 1227345    /usr/lib/libogg.so.0.5.3
b6016000-b6031000 r-xp 00000000 08:02 1229667    /usr/lib/libvorbis.so.0.4.0
b6031000-b6032000 r--p 0001a000 08:02 1229667    /usr/lib/libvorbis.so.0.4.0
b6032000-b6040000 rw-p 0001b000 08:02 1229667    /usrAborted[/FONT][/URL]



Thanks

---

### Post by kaligus on 2009-07-27
I just downloaded this awesome editor and installed it from the deb by the old fashioned double click.

8.10 intrepid 64 bit and not my development machine.

So far knock wood I have seen nothing but awesome.

Did you ever get this figured out?  I may or may not be able to help you figure it out but I still have an un-updated 8.04 hardy box sitting here I will be trying it out on later to see what happens (as soon as I get the hard drive issues figured out on that box).

---

