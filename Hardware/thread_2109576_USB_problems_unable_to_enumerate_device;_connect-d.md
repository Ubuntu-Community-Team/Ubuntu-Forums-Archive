---
title: "USB problems: unable to enumerate device; connect-debounce failed"
date: 2013-01-28
forum: Hardware
---

### Post by RyanGT on 2013-01-28
I have a problem with the USB ports on my laptop.  I think it is a grounding or static problem.  I have replace the LCD twice and I may not have put it back together exactly perfectly, but it mostly works.  Occasionally, when I connect my Bamboo Fun tablet, it is not regonized.  When that happens, the laptop will not suspend for several weeks.  In the past, the problem has eventually gone away.  I was googling around trying to debug the problem today when I found someone who said to go into terminal mode.  When I do that, two messages keep printing continually:

unable to enumerate USB device on port 1
connect-debounce failed, port 2 disabled

A screenshot is attached.

How do I tell the OS to ignore all pending USB connection attempts and whatever is in the back log and just wipe the slate clean?

Thanks,

Ryan

---

### Post by RyanGT on 2013-01-29
So, I accidentally, unintentionally solved this problem in a not very fulfilling way.  In order to solve a different problem, I booted the computer temporarily into Windows and I plugged a USB flashdrive in.  The flashdrive and USB port worked fine in Windows.  The next time I rebooted into Ubuntu, the scrolling messages were gone and the computer went into and out of suspension without any problems.

---

