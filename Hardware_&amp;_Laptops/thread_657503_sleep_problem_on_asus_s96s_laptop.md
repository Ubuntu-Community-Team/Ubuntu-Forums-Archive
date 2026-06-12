---
title: "sleep problem on asus s96s laptop"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by hhpeter on 2008-01-03
Hi there
I have a asus s96s laptop with nvidia 8600gs, intel 4965a/g/n wireless running ubuntu 7.10 with compiz fusion...I have problems with sleep option:
 
1.If I click on power button and then click on suspend it suspends nice and wakes up nice but no wireless....after doing some searches in this forum I modified this file etc/default/acpi-support  as follows:
from
MODULES_WHITELIST=""
to
MODULES_WHITELIST="iwl4965"
now when i resume from suspend my wireless works(just need to click on the wireless icon to connect again)
 
2.If I setup in power management to put to sleep my computer after lets say 10 minutes it goes to sleep but when I press on the keypad to wake it up it just goes blank screen nothing works and I need to hard reboot by pressing power button on the laptop for 5 seconds
 
Can anyone help me with this issue ? I searched on this forum and tried every solution with no luck please help me...

---

### Post by hhpeter on 2008-01-04
did I posted in the wrong section???

---

