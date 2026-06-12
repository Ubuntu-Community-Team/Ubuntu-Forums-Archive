---
title: "Gutsy: Lid closing and reopening hangs computer"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by gspr on 2007-10-19
Correction: This post is no longer valid. I found out that the opening and closing of the lid had nothing to do with the problem, and the disabling of the ACPI event had no effect. A post correctly describing the problem can be found at: [http://ubuntuforums.org/showthread.php?p=3569961#post3569961](http://ubuntuforums.org/showthread.php?p=3569961#post3569961)

IGNORE THE BELOW:
---
After an upgrade to Gutsy, closing and reopening the lid on my Toshiba Tecra A2 laptop two times (!) causes the screen to remain black and the computer to become unresponsive to any input when opening the lid the second time. Only solution is power cycle. The problem did not exist in Feisty.

It is easy to work around this by disabling the line
```
action=/etc/acpi/lid.sh
```
in /etc/acpi/events/lidbtn, but I'm just letting people know still.

The symptoms are similar to what someone experienced [1] in Edgy.


[1] [http://ubuntuforums.org/showthread.php?t=353446](http://ubuntuforums.org/showthread.php?t=353446)

---

