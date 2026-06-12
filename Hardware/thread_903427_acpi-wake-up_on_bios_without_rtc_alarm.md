---
title: "acpi-wake-up on bios without rtc alarm?"
date: 2008-08-28
forum: Hardware
---

### Post by RENE76 on 2008-08-28
Hi, I have a hp compaq dc5100MT desktop with the bios 786C2 version 1.09 installed. The bios does not include a rtc wake up alarm, but rather a bios startup menu:
MONDAY........ENABLE/DISABLE
TUESDAY.......ENABLE/DISABLE
WEDNESDAY.....ENABLE/DISABLE
THURSDAY......ENABLE/DISABLE
FRIDAY........ENABLE/DISABLE
SATURDAY......ENABLE/DISABLE
SUNDAY........ENABLE/DISABLE
TIME..........HH:MM
Is it possible for linux to utilize this bios startup for acpi-wake-up? Or will another bios version comply with ubuntu's acpi-wake-up? Any other solutions?
I plan to use the desktop for mythtv, and would like it to wake-up and shutdown according to the scheduled recordings.

---

### Post by Cuppa-Chino on 2008-08-29
just try.

see this page for guidance in general : 
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake")

for your info on my mainboard I had to DISABLE RTC in the BIOS so that the wakeup function could roam freely and work

---

### Post by RENE76 on 2008-08-29
The bios does not allow for enabling/disabling of "wake up on rtc" or anything similar. It only presents the "bios power on menu" I illustrated above.

I have tried acpi wiki and the nvram wiki without any success. I have updated the bios version to 1.09a and change the settings of the bios still with no success.

Does mythubuntu have other alternatives regarding automated wake up / shutdown?

---

