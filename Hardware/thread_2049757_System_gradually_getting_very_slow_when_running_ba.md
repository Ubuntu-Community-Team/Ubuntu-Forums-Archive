---
title: "System gradually getting very slow when running battery"
date: 2012-08-29
forum: Hardware
---

### Post by michalt on 2012-08-29
I have freshly installed Ubuntu 12.04 64bit on the HP 4320 (i3, radeon) notebook and I have problem with gradual slowdown when running on battery. 

After about 3-5 minutes on battery power system becomes very slow and unresponsive. It's  especially laggy during music and video playback (which get broken  quickly). 

Htop shows more then 10 running processes in que and all core  threads are running 100%. Though no extraordinary processes shows, just  all the normal known processes eats much more resources then usually.  Clicking icon, moving windows, everything is very slow and it gets just  worse and worse. When AC power is connected back the system becomes  normal in matter of seconds or sometimes a minute.

I tried disable and enable most of the settings with laptop mode tools with no success.

Only thing which did really help was acpi=off kernel option. With  acpi=ht the problem got back. 

Any idea or recommendation, please?

(I already reported this problem before reinstall in older thread which seems dead no, so sorry for creating new.)

---

