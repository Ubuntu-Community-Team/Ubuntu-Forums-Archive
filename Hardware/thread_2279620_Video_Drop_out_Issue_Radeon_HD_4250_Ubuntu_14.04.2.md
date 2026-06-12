---
title: "Video Drop out Issue: Radeon HD 4250: Ubuntu 14.04.2"
date: 2015-05-24
forum: Hardware
---

### Post by cbaughman on 2015-05-24
Greetings:

I've got my Linux Box set up as a media server and directly connected via HDMI to my TV. Every so often it appears as if the signal is lost to the TV displaying the same message on the TV when I shut the system down. This only happens for about 1 second and the display returns, it seems to get more frequent the longer the server is on. A quick reboot seems to releave the symptoms temporary.

Any help would is very much appropriated.

Carl

Below are some basic system and graphics card data.

Radeon HD 4250
Ubuntu 14.04.2

```
# lspci -nnk | grep -i vga -A3
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4250] [1002:9715]
        Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
        Kernel driver in use: radeon
01:05.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series] [1002:970f]
```

```

#egrep -i " connected|card detect|primary dev" /var/log/Xorg.0.log
[   134.950] (II) RADEON(0): Output HDMI-0 connected 
```

---

