---
title: "Simple scan multiple page issue - Canon mf244dw"
date: 2018-03-28
forum: Hardware
---

### Post by ch6574 on 2018-03-28
Hello,

When scanning multiple pages from a Canon mf244dw via the LAN I only get the first page scanned, then an error message.

Running "simple-scan -d" and looking at the output I see the following:

```
[+123.87s] DEBUG: scanner.vala:1321: sane_read (7651) -> (SANE_STATUS_CANCELLED, 0)
[+123.87s] WARNING: scanner.vala:1337: Unable to read frame from device: Operation was cancelled
[+123.87s] DEBUG: scanner.vala:768: sane_cancel ()
[+123.87s] DEBUG: scanner.vala:771: sane_close ()

```

I do notice that the scanner is already feeding in the second page before the first page has completely rendered on screen - perhaps it's going too fast?

Thanks

---

### Post by jpberes on 2018-04-02
I personally got the same problems scanning multiple pages on my HP Deskjet 3055A ..
I installed afterwards gscan2pdf, now using this one, and this one works perfectly.
Maybe worth giving it a try ?
Kind regards,
JP

---

### Post by slickymaster on 2018-04-02
*Thread moved to **Hardware**.*

---

### Post by ch6574 on 2018-05-01
Still get the same issue. What frontend are you using (shown under preferences)?

---

