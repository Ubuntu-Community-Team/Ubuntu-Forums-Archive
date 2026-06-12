---
title: "Arts crashing on startup"
date: 2005-11-08
forum: General Help
---

### Post by Jeff Eklund on 2005-11-08
Hi!
Whenever I boot my computer and log inte KDE, the first thing that happens is that artsd sends the signal "11 - SIGSEGV" and gives me the following errorlog:
```
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
[New Thread -1209133376 (LWP 9944)]
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
#14 0x4d91f95e in __gnu_cxx::__pool<true>::_M_reclaim_block ()
   from /usr/lib/libstdc++.so.6
#15 0x4cb2139f in virtual thunk to Arts::SoundServerV2_stub::version() ()
   from /usr/lib/libsoundserver_idl.so.1
#16 0x4cb41040 in Arts::SampleStorageEntry_base::_IID ()
   from /usr/lib/libsoundserver_idl.so.1
#17 0x08106608 in ?? ()
#18 0x00000004 in ?? ()
#19 0x08104fb8 in ?? ()
#20 0x08106608 in ?? ()
#21 0x00000000 in ?? ()
#22 0xbfa03348 in ?? ()
#23 0x4cb2b1cc in ?? () from /usr/lib/libsoundserver_idl.so.1
#24 0xbfa03384 in ?? ()
#25 0xbfa03390 in ?? ()
#26 0xbfa03348 in ?? ()
#27 0x4cb222ac in virtual thunk to Arts::GSLPlayObject_base::_defaultPortsOut() const () from /usr/lib/libsoundserver_idl.so.1
#28 0xbfa03390 in ?? ()
#29 0x08106608 in ?? ()
#30 0x00000001 in ?? ()
#31 0x08104fb8 in ?? ()
#32 0x4cad7cd8 in ?? () from /usr/lib/libsoundserver_idl.so.1
#33 0x00000000 in ?? ()
#34 0xbfa03384 in ?? ()
#35 0xbfa0336c in ?? ()
#36 0x0816202c in ?? ()
#37 0x4ce28b30 in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#38 0x4cb159d2 in Arts::SoundServerStartup_base::_fromString ()
   from /usr/lib/libsoundserver_idl.so.1

```
This started happening right after I installed KDE 3.5 beta 2 on my Beezy machine.
Any ideas?
Thanks!

---

### Post by daller on 2005-11-08
There's a solution here:

[https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems](https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems)

---

### Post by Jeff Eklund on 2005-11-08
Thanks got it working! :D

---

