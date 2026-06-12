---
title: "epson stylus scaner RX620"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by eternaldeals on 2007-03-02
ok can anyone tell me how to setup this epson stylus photo scaner rx620
It works great with suse  10.2 but I need to get it working with ubuntu 6.10

---

### Post by eternaldeals on 2007-03-02
anyone here know how to get this scaner working.

---

### Post by cornelis1 on 2007-03-04
Look at this thread: [http://www.ubuntuforums.org/showthread.php?t=20992&highlight=epson]("http://www.ubuntuforums.org/showthread.php?t=20992&highlight=epson")
To get the scanner working as a normal user (not using "gksudo") I found out you also have to add: 

# Epson RX-620
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0811", MODE="664", GROUP="scanner"

to /etc/udev/rules.s/45-libsane.rules

I have the same printer scanner and it works very well with Edgy

---

### Post by gjtoth on 2007-03-04
> **cornelis1 said:**
> Look at this thread: [http://www.ubuntuforums.org/showthread.php?t=20992&highlight=epson]("http://www.ubuntuforums.org/showthread.php?t=20992&highlight=epson")
To get the scanner working as a normal user (not using "gksudo") I found out you also have to add: 

# Epson RX-620
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0811", MODE="664", GROUP="scanner"

to /etc/udev/rules.s/45-libsane.rules

I have the same printer scanner and it works very well with Edgy

Also works great in Feisty once that line is added.

---

