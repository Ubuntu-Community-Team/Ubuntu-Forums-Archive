---
title: "Evolution: Subscribe to Other User's ..."
date: 2008-08-12
forum: General Help
---

### Post by decoherence on 2008-08-12
I'm using Evolution to hook up to my work's Groupwise server, however one particular function seems to be broken. Subscribe to Other User's Folder/Calendar does absolutely nothing.

stderr and the debug file both say

```
evolution-shell-Message: Killing old version of evolution-data-server...

(evolution:13072): camel-groupwise-provider-WARNING **: Could not connect..failure connecting
```

However this appears right as soon as I start the program, not when I try to proxy to another user's folder/calendar. When I try to proxy, like I said, absolutely nothing happens, no messages to stderr or the debug file.

Tried doing a google search on the groupwise-provder-WARNING but didn't come up with anything encouraging.

Would GDB be useful in figuring out what's going on? I've always meant to play with that. Can anyone give me any pointers, if that is potentially a useful way to go?

thanks,

---

### Post by fluffman86 on 2008-09-25
I just noticed the same thing.  Also, nothing happens when I click permissions or when I try to publish calendar information.  Any ideas?

---

