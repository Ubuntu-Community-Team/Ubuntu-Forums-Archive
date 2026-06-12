---
title: "&quot;error 2&quot; when compiling."
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by SomeGuyDude on 2009-04-19
Just wondering if anyone could help with this.

Yeah it's an Arch thing but that forum's slow and I don't think this is at all Arch-specific. I'm compiling a package called firefox-pgo, and near the end I get this:

```
/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/netwerk/protocol/http/src/nsHttpConnectionMgr.cpp: In constructor ‘nsAutoMonitor::nsAutoMonitor(PRMonitor*)’:
/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/netwerk/protocol/http/src/nsHttpConnectionMgr.cpp:989: error: corrupted profile info: number of executions for edge 2-3 thought to be 15677
/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/netwerk/protocol/http/src/nsHttpConnectionMgr.cpp:989: error: corrupted profile info: number of executions for edge 2-5 thought to be -6
make[8]: *** [nsHttpConnectionMgr.o] Error 1
make[8]: *** Waiting for unfinished jobs....
/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/netwerk/protocol/http/src/nsHttpChunkedDecoder.cpp: In member function ‘nsresult nsHttpChunkedDecoder::ParseChunkRemaining(char*, PRUint32, PRUint32*)’:
/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/netwerk/protocol/http/src/nsHttpChunkedDecoder.cpp:127: warning: conversion to ‘unsigned int’ from ‘long int’ may alter its value
make[8]: Leaving directory `/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/ff-opt-obj/netwerk/protocol/http/src'
make[7]: *** [libs] Error 2
make[7]: Leaving directory `/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/ff-opt-obj/netwerk/protocol/http'
make[6]: *** [libs] Error 2
make[6]: Leaving directory `/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/ff-opt-obj/netwerk/protocol'
make[5]: *** [libs] Error 2
make[5]: Leaving directory `/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/ff-opt-obj/netwerk'
make[4]: *** [libs_tier_necko] Error 2
make[4]: Leaving directory `/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/ff-opt-obj'
make[3]: *** [tier_necko] Error 2
make[3]: Leaving directory `/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/ff-opt-obj'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla/ff-opt-obj'
make[1]: *** [build] Error 2
make[1]: Leaving directory `/tmp/yaourt-tmp-crew/aur-firefox-pgo/firefox-pgo/src/mozilla'
make: *** [profiledbuild] Error 2
==> ERROR: Build Failed.
    Aborting...
Error: Makepkg was unable to build firefox-pgo package.
```

Any ideas?

---

