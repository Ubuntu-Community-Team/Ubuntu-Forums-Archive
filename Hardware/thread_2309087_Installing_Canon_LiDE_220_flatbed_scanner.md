---
title: "Installing Canon LiDE 220 flatbed scanner"
date: 2016-01-07
forum: Hardware
---

### Post by Owen Thomas on 2016-01-07
Hello Ubuntu community.

I have just purchased a Canon LiDE 220 flatbed scanner so I can scan documents, only when I plug the scanner into a USB on my HP Laptop (which runs Ubuntu 14.04 LTS), nothing happens. Canon provides installation support only for Windows or Mac.

Can anyone help me work out what to do?

  Owen.

---

### Post by howefield on 2016-01-07
If you haven't already, read this this thread..

[http://ubuntuforums.org/showthread.php?t=2258489](http://ubuntuforums.org/showthread.php?t=2258489)

---

### Post by Owen Thomas on 2016-01-07
Thanks howefield for getting back to me.

I had a look at that page, but found that [this page]("http://gsusmonzon.blogspot.com.au/2015/06/canon-lide-220-in-ubuntu-1404.html") gave me concise instructions to follow, so follow them I did.

When not running as root I do lsusb and find the following: Bus 002 Device 002: ID 04a9:190f Canon, Inc.

I then [FONT=&quot]sudo chmod u+w /dev/bus/usb/002/002[/FONT]

Finally, I try to run xsane and a dialogue appears telling me that no devices are available.

When I run as root, xsane starts and I can appear to scan documents.

Any suggestions?

---

