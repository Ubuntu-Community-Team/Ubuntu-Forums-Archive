---
title: "Synaptic Touchpad and ACPI issues on battery"
date: 2008-05-12
forum: Hardware
---

### Post by Lexcel on 2008-05-12
I am a new user to Ubuntu, but have quite a bit of Linux experience, including Debian so if you have a suggestion, please do not be gun shy - but please don't be rude either!

Currently I have a Dell Laptop - Latitude D630 that is running the latest version of Ubuntu (8.04 LTS).  Everything is working great on AC power without any modifications to the kernel or kernel line; however, on battery power, I need to acpi=off (I have tried other acpi= but off is the only one that works) because if I do not two things happen:

1.  Mouse movements after about 30 seconds of inactivity become erratic.  I am sure and have seen plenty of posts regarding /var/log/messages output regarding disgarding data due to mouse being out of sync.

2.  Using the touchpad (Synaptics), will cause a kernel panic on the laptop.

Keep in mind that these two things only happen when acpi is on and on battery power.  This does NOT happen when on AC power.  If I use the acpi=off on battery power, it does not happen either.

I am not going to post a whole bunch of output for people to view but am treating this more as an exploring mission since I cannot find anything here or googled on this yet and wanted to see if anyone else has experienced this as of yet and if so, if you have resolved this issue or could make suggestions.  I do have a workaround but would prefer not to modify the kernel line each time I boot without power.  

Thanks for your consideration.

---

