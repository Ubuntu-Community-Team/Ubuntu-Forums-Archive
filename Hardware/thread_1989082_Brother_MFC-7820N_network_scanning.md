---
title: "Brother MFC-7820N network scanning"
date: 2012-05-28
forum: Hardware
---

### Post by tcamdg on 2012-05-28
Works fine in openSUSE, but not with Ubuntu. :confused:

Even sudo doesn't work for scanning over the network. Any help? I've installed the necessary Brother drivers, and it *should* work, but doesn't.

"No devices found." Even with sudo.

---

### Post by tcamdg on 2012-05-28
Figured it out... 

[http://ubuntuguide.org/index.php?title=MFC-7820N&redirect=no]("http://ubuntuguide.org/index.php?title=MFC-7820N&redirect=no")

Basically: 

[LIST=1]
[*]Install **libsane-utils** from the repositories and the **brscan2** (for this scanner model) driver from the Brother web site.
[*]Copy the [specified files]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101") under **/usr/lib64/** to **/usr/lib/**
[*]Per the [Brother FAQ]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101"), add the following two lines to the end of the device list in **/lib/udev/rules.d/40-libsane.rules**
```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
```
[*]Then add the scanner using: 
```
brsaneconfig2 -a name=SCANNER model=MFC-7820N ip=192.168.xx.xx
```
[*]It may (or may not) be necessary to reboot.
[/LIST]

---

