---
title: "kde 3.5 final ,not so final?"
date: 2005-12-01
forum: General Help
---

### Post by blakken on 2005-12-01
all through kde 3.5 versions (beta2,rc2,rc1 nd final) I install the sound bug problem isn't yet solved,each time I make for instance a system notification i got kde crash signal ,obviously rc1 was solved by replacing art library  with the one from 3.4 ,shall I have to once again go back?
:mad: 
for information here is the backtrace stuff ,any idea what's wrong?
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1219246400 (LWP 9669)]
[New Thread -1289847888 (LWP 9687)]
[New Thread -1281455184 (LWP 9686)]
[New Thread -1271174224 (LWP 9685)]
[New Thread -1258681424 (LWP 9684)]
[New Thread -1246041168 (LWP 9683)]
[New Thread -1237378128 (LWP 9682)]
[New Thread -1228985424 (LWP 9681)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#13 0xb7b47363 in Arts::PlayObject_base::_create ()
   from /usr/lib/libkmedia2_idl.so.1
#14 0x0805aa5f in ?? ()
#15 0xbfda5e4c in ?? ()
#16 0xbfda5e38 in ?? ()
#17 0x00000020 in ?? ()
#18 0xb7c99900 in __malloc_initialize_hook ()
   from /lib/tls/i686/cmov/libc.so.6
#19 0x00000000 in ?? ()
#20 0xb7d9d2b8 in ?? () from /usr/lib/libstdc++.so.6
#21 0x00da5e38 in ?? ()
#22 0xb7d99cb8 in ?? () from /usr/lib/libstdc++.so.6
#23 0xbfda5ec4 in ?? ()
#24 0x0000000c in ?? ()
#25 0xbfda5e68 in ?? ()
#26 0xb7d52a00 in std::string::assign () from /usr/lib/libstdc++.so.6
#27 0xb7b5402f in Arts::StreamPlayObject_stub::inputStream ()
   from /usr/lib/libkmedia2_idl.so.1
#28 0xb7a0012f in Arts::Object_skel::_dispatch () from /usr/lib/libmcop.so.1
#29 0xb7a009e1 in Arts::Dispatcher::handle () from /usr/lib/libmcop.so.1
#30 0xb7a0260a in Arts::Connection::receive () from /usr/lib/libmcop.so.1
#31 0xb7a027fd in Arts::SocketConnection::notifyIO ()
   from /usr/lib/libmcop.so.1
#32 0xb79a1dd4 in Arts::StdIOManager::processOneEvent ()
   from /usr/lib/libmcop.so.1
#33 0xb797d52b in Arts::StdIOManager::run () from /usr/lib/libmcop.so.1
#34 0xb797d3c5 in Arts::Dispatcher::run () from /usr/lib/libmcop.so.1
#35 0x0806032f in ?? ()
#36 0xbfda8370 in ?? ()
#37 0x0000003b in ?? ()
#38 0xbfda8498 in ?? ()
#39 0x0806044f in ?? ()
#40 0x080f8de0 in ?? ()
#41 0x05556bcf in ?? ()
#42 0xbfda83e0 in ?? ()
#43 0xb7a563ec in ?? () from /usr/lib/libmcop.so.1
#44 0x00000001 in ?? ()
#45 0xbfda83a4 in ?? ()
#46 0x00000000 in ?? ()
#47 0xb7da8a20 in ?? ()
#48 0x080fb5d0 in ?? ()
#49 0x080f8ea8 in ?? ()
#50 0x00000008 in ?? ()
#51 0x080fb7d8 in ?? ()
#52 0x080fb7d8 in ?? ()
#53 0x080fb9d8 in ?? ()
#54 0x080f8eb4 in ?? ()
#55 0x080fb7d8 in ?? ()
#56 0x080fb7d8 in ?? ()
#57 0x080fb9d8 in ?? ()
#58 0x080f8eb4 in ?? ()
#59 0x00000000 in ?? ()
#60 0x00000000 in ?? ()
#61 0x00000000 in ?? ()
#62 0x080f8ed0 in ?? ()
#63 0x00000008 in ?? ()
#64 0x080fb9e0 in ?? ()
#65 0x080fb9e0 in ?? ()
#66 0x080fbbe0 in ?? ()
#67 0x080f8edc in ?? ()
#68 0x080fba28 in ?? ()
#69 0x080fb9e0 in ?? ()
#70 0x080fbbe0 in ?? ()
#71 0x080f8edc in ?? ()
#72 0x081c9ca8 in ?? ()
#73 0x081ca128 in ?? ()
#74 0x081ca4a8 in ?? ()
#75 0x081c4358 in ?? ()
#76 0x081dacf0 in ?? ()
#77 0x080f9edc in ?? ()
#78 0xbfda8401 in ?? ()
#79 0x00000000 in ?? ()
#80 0x080fca80 in ?? ()
#81 0x080fc700 in ?? ()
#82 0x08107a08 in ?? ()
#83 0x080fc0f0 in ?? ()
#84 0x080ffff8 in ?? ()
#85 0x080fca50 in ?? ()
#86 0x00000000 in ?? ()
#87 0x087a64f0 in ?? ()
#88 0x0812baf8 in ?? ()
#89 0x00000000 in ?? ()
#90 0x08115338 in ?? ()
#91 0x08116a30 in ?? ()
#92 0x080fb610 in ?? ()
#93 0x08119778 in ?? ()
#94 0x00000000 in ?? ()
#95 0xbfda8438 in ?? ()
#96 0x0812baf8 in ?? ()
#97 0x00000000 in ?? ()
#98 0x08115338 in ?? ()
#99 0x08116a30 in ?? ()
#100 0x0812baf8 in ?? ()
#101 0x00000000 in ?? ()
#102 0x08115338 in ?? ()
#103 0x08116a30 in ?? ()
#104 0x080512c8 in ?? ()
#105 0x0807405c in std::string::_Rep::_S_empty_rep_storage ()
#106 0x080fb5b0 in ?? ()
#107 0x080bb69c in ?? ()
#108 0x080bb69c in ?? ()
#109 0x080bb69c in ?? ()
#110 0x080bb69c in ?? ()
#111 0x080bb69c in ?? ()
#112 0x080bb69c in ?? ()
#113 0x080bba84 in ?? ()
#114 0xbfda8498 in ?? ()
#115 0x0806b043 in Arts::SoundServerV2_skel::~SoundServerV2_skel ()
#116 0xb7b82ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#117 0x080548d1 in ?? ()

---

### Post by ausm on 2005-12-01
I tried loading last night and managed to really mess up my system :( I going to have to restore using my backup. I think I am going to wait until the Next version of Kubuntu comes out to use it.

Ausm

---

### Post by lerrup on 2005-12-02
blakken - have you tried playing around with the sound architecture selection in the system settings panel?  It worked for me.

ausm -any further details?  If you have a prob with 3.5 you could just delete the repository from your list and reinstall kubuntu-desktop.

---

### Post by ausm on 2005-12-02
[QUOTE=lerrup]blakken - have you tried playing around with the sound architecture selection in the system settings panel?  It worked for me.

ausm -any further details?  If you have a prob with 3.5 you could just delete the repository from your list and reinstall kubuntu-desktop.[/QUOTE]

Thanks for the tip I will try that when i get home tonight.

Ausm

---

### Post by shakin on 2005-12-02
[QUOTE=lerrup]blakken - have you tried playing around with the sound architecture selection in the system settings panel?  It worked for me.

ausm -any further details?  If you have a prob with 3.5 you could just delete the repository from your list and reinstall kubuntu-desktop.[/QUOTE]

You'll probably need to force versions on each of the kde packages.

---

### Post by blakken on 2005-12-03
lerrup thanx for your help ,I tried several combinations but in fact it didn't change  ,what's your configuration?;)

---

