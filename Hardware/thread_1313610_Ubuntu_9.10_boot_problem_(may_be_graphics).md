---
title: "Ubuntu 9.10 boot problem (may be graphics)"
date: 2009-11-03
forum: Hardware
---

### Post by apurvas84 on 2009-11-03
Hello,

I installed Ubuntu 9.10 3 days back and things worked fine. I have dual boot setup and GRUB loads properly.
Yesterday, I tried upgrading the proprietary nVIDIA 3D graphics drivers from 173 to 185 (recommended). The installation failed and I didn't think much of it.
When I booted into Ubuntu later, I got a flashing screen asking for my login. This was in the command prompt. So the graphical interface did not show up.
When I try typing, it sometimes recognizes the keystroke and sometimes does not. So, entering my password is impossible.
I am a novice about all things Linux so any help will be greatly appreciated.

Thanks

---

### Post by theozzlives on 2009-11-03
Could be, I have a nVIDIA GeForce 6 series and originally booted to a white screen. I downloaded the driver from nVIDIA and booted recovery, root prompt. After installing manually, it works fine.

---

### Post by apurvas84 on 2009-11-04
Manual install instructions please?

---

### Post by preludelinux on 2009-11-23
I have the same problem, i have upgraded from the lts version too 9.10 once reinstalling the nvidia drivers i get a flashy screen. but if u drop to a maintenance terminal before and modprobe -i nvidia it boots up correctly into gnome. it starts flashing at the dkms configuration and prevents text input into the system and x server will not start. tried manual listing nvidia in /etc/modules and did not help. any suggestions appears it has to do with module insertion of the nvidia driver. At some point i may do a fresh install and try to see if it is reproducible.

---

