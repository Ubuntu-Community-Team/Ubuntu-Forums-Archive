---
title: "hibernate's not working when laptop lid is closed"
date: 2010-05-07
forum: Hardware
---

### Post by trawler on 2010-05-07
I have an HP DV4000 laptop, with a faulty cd drive. I had to install ubuntu on the hard drive via a usb case, connected to my pc.
My problem is that some laptop specific features don't seem to work. 
Even though the power settings are configured correctly (hibernate when lid is closed) nothing really happens.
For example, if i play something while closing the lid, it'll continue on playing.

I checked "cat /proc/acpi/button/lid/LID0/state" and saw that it detected the lid as open, but it also does that when the lid is closed... (checked it through ssh).

I'm assuming that since I installed ubuntu from a PC, some laptop-specific packages were not installed, how can I solve this issue?

---

