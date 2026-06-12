---
title: "System Settings / Appearance crashes X w/ Compiz"
date: 2008-10-02
forum: General Help
---

### Post by skullmunky on 2008-10-02
When I go to System Settings->Appearance, my X session suddenly quits and goes back to the login screen.  Most other windows and applications all work fine.

Using KWin everything's all right, it's only with Compiz as the window manager.

Weird!

Ah, I think this is the error from the log:

```


Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7fce420]
2: /usr/bin/X(ProcPolyPoint+0x14a) [0x808aa9a]
3: /usr/bin/X [0x815075e]
4: /usr/bin/X(Dispatch+0x2cf) [0x808d8df]
5: /usr/bin/X(main+0x48b) [0x807471b]
6: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d4b450]
7: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

```

Does that mean anything to anyone...?

---

