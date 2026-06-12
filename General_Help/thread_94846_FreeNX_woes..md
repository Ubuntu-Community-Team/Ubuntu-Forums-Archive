---
title: "FreeNX woes."
date: 2005-11-25
forum: General Help
---

### Post by boakes on 2005-11-25
Greetings all, this is my first post.

I had freenx working for about a week, on Breezy.  I did some updates and now all of a sudden NX will start X but it will quickly disappear.

[PHP]NXPROXY - Version 1.5.0

Copyright (C) 2001, 2005 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '3744'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image cache parameters 1/1/32768KB.
Info: Using adsl link parameters 8192/8/10/50.
Info: Using pack method '16m-jpeg-7' with session 'unix-gnome'.
Info: Using ZLIB data compression level 3.
Info: Using ZLIB data threshold set to 32.
Info: Using ZLIB stream compression level 6.
Info: Using remote ZLIB data compression level 3.
Info: Using remote ZLIB stream compression level 6.
Info: No suitable cache file found.
Info: Starting X protocol compression.
Info: Established X server connection.
Info: Using shared memory support in X server.
Info: End of session requested by remote proxy.
Info: Shutting down the link and exiting.[/PHP]

Note:  I did say it was working then apparently some update bjorked it again.  This is becoming rather frustrating any advise would be appreciated.

---

### Post by boakes on 2005-11-25
Ok, for some weird reason, it's now working.  I don't understand what's going on, I did nothing that I'm aware of to fix it.

---

### Post by nihilocrat on 2005-11-28
I'm getting the exact same problem, and I'm not sure how to fix it after restarting, moving stale 'running' sessions, etc.

Is it a problem that I'm running NX 1.4.0 on the server side and the 1.5.0 client? Apt-get says freenx is in its latest version (after apt-get update).

---

