---
title: "[SOLVED] battery drains when Lenovo X300 is hibernating"
date: 2008-11-28
forum: Hardware
---

### Post by phorminx on 2008-11-28
I have Ubuntu 8.10 installed on a Lenovo X300. It mostly works fine. But hibernation drains the battery (about 1% per hour). The laptop is dual boot with windows XP installed as well. Initially XP gave me the same problem till I learned that I need to switch off wake-on-lan both in the bios and and in the XP device manager for the ethernet card. So yes, under XP the culprit was the ethernet card and I expect it is the same under ubuntu. Of course, switching off wake-on-lan in the bios affects both XP and ubuntu. But I do not know what is the equivalent step to switching off wake-on-lan in the XP device manager. (It's beyond my knowledge why both of these two steps are required at all.)

Any help is appreciated!

---

### Post by sdennie on 2008-11-28
The top of this page explains how to turn off wake on lan: [http://www.lesswatts.org/tips/ethernet.php](http://www.lesswatts.org/tips/ethernet.php)

---

### Post by phorminx on 2008-11-28
> **vor said:**
> The top of this page explains how to turn off wake on lan: [http://www.lesswatts.org/tips/ethernet.php](http://www.lesswatts.org/tips/ethernet.php)

Perfect, this was what I was looking for!

---

