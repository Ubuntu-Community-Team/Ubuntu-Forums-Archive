---
title: "USB devices causes Internet to be accessed"
date: 2008-11-21
forum: Hardware
---

### Post by Gannin on 2008-11-21
Every time I plug in a USB device, wether it's a printer or an audio device or anything else, there's always a data burst, an upload and download burst, between my computer and the Internet.  My computer uploads about 10k of data or so, and downloads about 50k of data or so, every time.  What gives?

If I do a netstat right after I plug in a USB device when the Internet is being accessed as I described, this is what it gives me:

udp        0      0 Mycomputer.local:33839   dns-redirect-lb-:domain ESTABLISHED

Of course the local port number changes every time.  Why is a DNS server apparently being accessed when a USB device is plugged in?

---

### Post by Azure.Rise on 2008-11-21
Trojan stealing your data? That'd be weird though if you're running Linux.

---

### Post by Gannin on 2008-11-21
This is a fairly fresh install of Intrepid, with all current updates applied.

---

### Post by Yezinki on 2008-11-21
Does the printer or audio device have a wireless/ BT connectivity too?

---

### Post by Gannin on 2008-11-21
Nope, these are purely non-networkable devices.

---

### Post by Yezinki on 2008-11-21
Do a online virus scan for Ubuntu.........

[http://www.kaspersky.com/virusscanner](http://www.kaspersky.com/virusscanner)

Just to be sure that your machine is clean.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-21
[http://www.kaspersky.com/support/linux_file57?level=2](http://www.kaspersky.com/support/linux_file57?level=2)

---

### Post by Gannin on 2008-11-21
My system appears to be clean.

---

### Post by Yezinki on 2008-11-21
Gannin,

I apologize that I wouldn't be of much help since I quit Ubuntu & am using windows again....

Regards,

Yezinki.

---

### Post by Gannin on 2008-11-21
After doing some work with the Ubuntu team this has been identified as a bug.

---

