---
title: "Touchpad not showing up in xinput on Lenovo ideapad flex 5 AMD."
date: 2021-01-08
forum: Hardware
---

### Post by 0x54 on 2021-01-08
[SIZE=2][FONT=arial]I  have recently installed ubuntu in a dual boot configuration on my  laptop and have not yet managed to get my touchpad to be recognized by  ubuntu. No results on xinput, lshw etc. I have already tried many  possible solutions like grub flags, blacklisting i2c_hid modules and  installing synptics drivers. Most of the numerous other posts about this  issue, it seems to be quite common, either have no solution or mention  to manually upgrade the kernel of ubuntu, which I would not like to do  as I do not know enough about that. (Since I wrote this post ubuntu updated the kernel (from 4.x to 5.8) however nothing changed)
[/FONT][/SIZE]
[SIZE=2][FONT=arial]
I have also forgotten to register the mok during the first reboot if that matters, however ubuntu tells me I have no third party drivers installed.

Any help would be appreciated[/FONT][/SIZE]

Update: I can see a ps/2 mouse in dmesg
[COLOR=#D7DADC]
[/COLOR]"mousedev: PS/2 mouse device common for all mice"[COLOR=#D7DADC]
[/COLOR]

---

