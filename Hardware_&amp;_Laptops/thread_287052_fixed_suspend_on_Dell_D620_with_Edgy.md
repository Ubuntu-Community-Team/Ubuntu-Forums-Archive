---
title: "fixed suspend on Dell D620 with Edgy"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by dro0g on 2006-10-28
Suspend worked for me about 90% time on 6.06. However, after upgrading, it was back to hanging either while suspending or while coming back.

I followed the instructions here to change /etc/default/acpi-support with some modifications:

[http://www.ubuntuforums.org/showthread.php?t=201960&highlight=suspend](http://www.ubuntuforums.org/showthread.php?t=201960&highlight=suspend)

SAVE_VBE_STATE should be set to false like in the post above

POST_VIDEO and USE_DPMS however should be set to true

DOUBLE_CONSOLE_SWITCH should also be set to true


this has worked for me the couple times that i've tested it so far.

---

### Post by dro0g on 2006-10-29
Spoke too soon. The HDD doesn't come back on-line after suspends about half the time. I tried setting RESET_DRIVE=true, but that doesn't seem to have had any effect.

---

### Post by strawman on 2006-10-29
my hp nc8000 also does not resume from suspend since installing (fresh) edgy.
sounds like it's a problem with the latest kernel.

---

### Post by cmaxo on 2006-10-30
I followed these instructions and standby works great now.

[https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620)

---

### Post by strawman on 2006-11-02
thanks cmaxo, that works for me also but i didn't have to put my wireless ipw2100 module in /etc/default/acpi-support.

good to have suspend working again:)

---

