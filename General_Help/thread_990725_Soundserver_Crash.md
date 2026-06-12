---
title: "Soundserver Crash"
date: 2008-11-23
forum: General Help
---

### Post by TransitMan on 2008-11-23
KDE 3.5.10, *buntu 8.04, either in Kubuntu or GNOME I have recently been experiencing a Soundserver (artsd) crash. Can't find anything on this except older posts from Breezy Badger. 
Below is the log file:
```
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
[New Thread 0xb74d46c0 (LWP 7755)]
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
#4  0xb7b96811 in fwrite () from /lib/tls/i686/cmov/libc.so.6
#5  0x08056d13 in ?? ()
#6  0x080581f2 in ?? ()
#7  0x0805f98b in ?? ()
#8  0x080666ed in ?? ()
#9  0xb79f3060 in Arts::ObjectManager::create () from /usr/lib/libmcop.so.1
#10 0xb7f09fd6 in Arts::SoundServerV2_base::_create ()
   from /usr/lib/libsoundserver_idl.so.1
#11 0xb7f105dd in Arts::SoundServerV2::_Creator ()
   from /usr/lib/libsoundserver_idl.so.1
#12 0x0805db17 in ?? ()
#13 0xb7b51450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#14 0x08054ad1 in ?? ()
```

Any help or guidance in getting this resolved would be aprreciated.
I have already rolled back and upgraded the arts files.

---

