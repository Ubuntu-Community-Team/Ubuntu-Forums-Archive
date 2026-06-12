---
title: "Fujitsu Siemens Amilo Pi 3540 compatibility"
date: 2009-04-05
forum: Hardware
---

### Post by cynop on 2009-04-05
Hello, i am thinking of buying a Fujitsu Siemens Amilo Pi3540. Has anyone tried installing 8.10 on it? any incompatibility problems i should know?

---

### Post by rusart on 2009-04-14
Good compatible. Only one problem is with micropone, but i think it's fixible. Kubuntu 9.04 beta.

---

### Post by rusart on 2009-04-16
Problem with microphone solved by upgrading alsa to 1.0.19 with this script:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Oops, one more problem. I can't connect to D-Link DWL-2100AP with wpa-security and default params. It fixes by set AT ACCESS POINT "Cypher Method" from AUTO to AES. May be need to be reported?

---

### Post by drpyro on 2009-06-25
there is a bug width the special keys... especially width the sound conrol, it enter on iterate loops when rising or muting the sound via keyboard :( [*Bug* #365991]("https://bugs.launchpad.net/ubuntu/+bug/365991")

---

### Post by schurl on 2009-07-03
I experienced problems with 4GB Ram in combination with 64bit Linux. Tested with Ubuntu 9.04 (desktop and server). I experienced frequent crashes resulting in automatic reboot. This has been confirmed by many other users (Win and Linux). For Linux there is a workaround by specifying the 'mem=4096' boot parameter. After that the system runs stable but it seems that it is only possible to use 3GB in this case. Without the boot param free shows all the 4GB but crashes frequently.

---

