---
title: "COM1 serial port not available on WINE or Win4Lin please help"
date: 2008-11-06
forum: Hardware
---

### Post by vk4ebp on 2008-11-06
Running Ubuntu 8.10 ona Dell D610 laptop. I need to use a small WIndows program for controlling a hamradio handheld. All hardware and sofware works OK on native Windows installation.
When running the software either on Wine or Windows/Win4lin I get a message that 'port uavailable, check connections' etc.
Added a symlink to dosdevices folder linking ttyS0 to com1 to no effect. And the Windows/win4lin installation is seeing COM1 in device manager.
Going through the forums it appears that it's a common problem. Anyone can help please?
Jan

---

### Post by vk4ebp on 2008-11-09
bump

---

### Post by herrdoktor330 on 2008-12-07
I'm having a similar problem on 8.04 with an FTA program. When I look up available com ports to use, I get no options. I did the symbolic link in the /dosdevices folder per instruction by winehq.org, but it's still not working.

Is there something I'm missing?

---

### Post by hoofdbaas on 2009-12-11
After a few hours trying I ended up with chown the com1 file in dosdevices
This worked for me I can use my GPS now in Oziexplorer

---

