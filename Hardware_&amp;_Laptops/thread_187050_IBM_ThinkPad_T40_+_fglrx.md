---
title: "IBM ThinkPad T40 + fglrx"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by Infeliz on 2006-06-02
Hello 

I've tried to install 3D-acceleration, but it doesnt work.

I've ATI Mobility 9000 FireGL (M9) 

I get errors when I am trying to install ATIs Proprietary Drivers

Here is my output:

kimmo@dapper:~$ cat /var/log/Xorg.0.log |grep EE
Current Operating System: Linux dapper 2.6.15-23-686 #1 SMP PREEMPT Tue May 23 14:03:07 UTC 2006 i686
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

kimmo@dapper:~$ dmesg | grep fglrx
[4294705.223000] [fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
[4294705.223000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294706.922000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294706.923000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294706.923000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294706.924000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294707.009000] [fglrx] total      GART = 268435456
[4294707.009000] [fglrx] free       GART = 252440576
[4294707.009000] [fglrx] max single GART = 252440576
[4294707.009000] [fglrx] total      LFB  = 25505792
[4294707.009000] [fglrx] free       LFB  = 13611008
[4294707.009000] [fglrx] max single LFB  = 13611008
[4294707.010000] [fglrx] total      Inv  = 0
[4294707.010000] [fglrx] free       Inv  = 0
[4294707.010000] [fglrx] max single Inv  = 0
[4294707.010000] [fglrx] total      TIM  = 0

Any ideas?:)

---

### Post by spotman on 2006-06-02
did you modify your /etc/X11/xorg.conf to use the new driver?

if you open up that file (use sudo, you need root permissions to modify it), you need to scroll down to where it says "Driver    Vesa" (It might say anything like fbdev, or fglrx), and its past where the drivers are for your mouse/and or wacom, etc.   

You can also enable the drive automatically by going to a terminal and typing sudo aticonfig --initial

Judging from your dmesg post, it looks like the driver is loaded ok.  Once your in X mode, type fglrxinfo to see if its loaded correctly.

---

### Post by Infeliz on 2006-06-04
Should fglrx reposities drivers work in Radeon 9000 Mobility?

---

