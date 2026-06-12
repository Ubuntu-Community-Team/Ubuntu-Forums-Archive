---
title: "Monitor switch on HP Pavillion DV 9055 crashes X"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by sybren on 2007-01-10
Hi folks,

I've got Kubuntu Edgy running on my new HP Pavillion DV9055 laptop. It runs fine most of the time. However, I also want to be able to use it for presentations, which means I need to turn on the VGA output. If I press FN+F4 on the laptop it should switch monitors (works fine on Windows XP) but all it does is crash X:

```

  Backtrace:
  0: /usr/bin/X(xf86SigHandler+0x81) [0x80c3971]
  1: [0xffffe420]
  2: /lib/tls/i686/cmov/libc.so.6(__strtoul_internal+0x3f) [0xb7de07df]
  3: /usr/bin/X [0x80e5a27]
  4: /usr/bin/X(xf86HandlePMEvents+0x3b) [0x80d264b]
  5: /usr/bin/X(xf86Wakeup+0x153) [0x80c4e23]
  6: /usr/bin/X(WakeupHandler+0x59) [0x808a5c9]
  7: /usr/bin/X(WaitForSomething+0x1b9) [0x8194489]
  8: /usr/bin/X(Dispatch+0x82) [0x8086832]
  9: /usr/bin/X(main+0x485) [0x806e715]
  10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7dc88cc]
  11: /usr/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

  Fatal server error:
  Caught signal 11.  Server aborting

```

I've attached the full log in gzip format (the forum didn't allow a plain-text attachment, it was too large) for those who are interested.

Hopefully someone can help me work this out. I've searched the forums and Google, but I can't find anything relating - I'm rather ](*,)

---

