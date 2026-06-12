---
title: "Touchpad not detected throughout Ubuntu 20.04 up to 21.04 - Ideapad flex 5 14ARE05"
date: 2021-08-24
forum: Hardware
---

### Post by 0x54 on 2021-08-24
I have already made a few posts but it has been a while now so I though I might check whether there is some new information on the topic.
I am currently on ubuntu 21.04 with kernel 5.11.

The touchpad does not show up in xinput or libiinput list-devices.

The only thing I have on the touchpad is this:

[    0.004755] ACPI: SSDT 0x00000000C968F000 007216 (v02 LENOVO AmdTable 00000002 MSFT 04000000) 
[    0.679502] i2c_hid i2c-MSFT0001:00: supply vdd not found, using dummy regulator 
[    0.679525] i2c_hid i2c-MSFT0001:00: supply vddl not found, using dummy regulator

Although the latter two messages do not show up with mainline kernel 5.13. 
I have heard thing in a garuda-linux forum that kernel 5.14 may fix this but since this is ubuntu it might take at least till October for that to be released in 21.10, if it won't be 5.13. 
I might try to manually install 5.14 at some point though. 

I just want to say one more thing: The issue is specific to this very model and touchpad. 
Solutions for the 15ARE05 do not work.

Any help would be appreciated. I would really like to properly use my laptop and Linux.

---

