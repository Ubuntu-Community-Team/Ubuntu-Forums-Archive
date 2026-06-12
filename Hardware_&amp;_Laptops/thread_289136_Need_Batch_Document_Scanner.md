---
title: "Need Batch Document Scanner"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by SuperMike on 2006-10-30
Anyone know a document scanner product supported by the Ubuntu Dapper's version of the SANE drivers and that can feed in multiple documents? I purchased the HP Scanjet 8390 for a PHP-based imaging project I wanted to develop, thinking that SANE could talk to most stuff on a common protocol, but boy was I wrong. Fifteen hundred dollars later, I'm looking at returning this thing.

Note I also need to get something new. My employer won't purchase anything used or after-market.

Something USB would be more preferable.

---

### Post by SuperMike on 2006-11-11
Problem solved. I discovered that HP started using Avision chipsets after a certain timeframe, and that a guy in Germany (Rene Rebe of ExactCODE) had been making these SANE drivers for awhile now. I emailed him and mentioned the issue, and he worked with me on Windows XP and a USB sniffer to determine how the chipset works. He then wrote a C driver for it and it will more than likely appear in the SANE backend drivers in the very near future. His driver works beautifully on Ubuntu.

To get the latest Avision backend to perhaps support your HP Scanjet, go to here, or to try to contact Rene, go to here:

[http://www.exactcode.de/oss/avision/feedback.html]("http://www.exactcode.de/oss/avision/feedback.html")

---

