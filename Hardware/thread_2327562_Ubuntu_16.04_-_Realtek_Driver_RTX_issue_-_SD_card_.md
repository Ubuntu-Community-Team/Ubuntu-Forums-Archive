---
title: "Ubuntu 16.04 - Realtek Driver RTX issue - SD card reader NOK"
date: 2016-06-12
forum: Hardware
---

### Post by Fluxflixflex on 2016-06-12
Hi guys,

I am pretty newbie with all the driver's and hardware stuf, but i have an issue that have been bothering me alot since I upgraded my ubuntu to 16.04.

My Realtek SD reader would no long work, i've made some research and so far nothing working came up.
It seems that SD cards are no longer readed :


```

florian@florian-UX32VD:~$ uname -r
4.4.0-24-generic

florian@florian-UX32VD:~$ lsusb
Bus 002 Device 003: ID 04f2:b330 Chicony Electronics Co., Ltd Asus 720p CMOS webcam
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller**
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



florian@florian-UX32VD:~$ lspci 
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation 3rd Gen Core Processor Thermal Subsystem (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 7 Series/C210 Series Chipset Family Thermal Management Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
florian@florian-UX32VD:~$ 



florian@florian-UX32VD:~$ sudo modprobe rts5139
florian@florian-UX32VD:~$ sudo modprobe rtsx_usb_sdmmc 
florian@florian-UX32VD:~$ sudo modprobe rtsx_usb_ms 
florian@florian-UX32VD:~$ 
florian@florian-UX32VD:~$ 



```

Strange that it does not appear in the lspci command..

I Tried the following solution :
[https://github.com/asymingt/rts5139](https://github.com/asymingt/rts5139)

But still no chance.
I've made a bit of research and it seems that RTSX driver embeds the RTS5139 driver ([https://github.com/oppo-source/R7f-4.4-kernel-source/blob/master/drivers/staging/rts5139/Kconfig](https://github.com/oppo-source/R7f-4.4-kernel-source/blob/master/drivers/staging/rts5139/Kconfig))

but still nothing came up after the sudo modprobe rtsx_usb_sdmmc or usb_ms... reload and so on..

If anyone has an idea what could be next step, i would really appreciate it :)


Thank you all and have a great day ahead.

Florian

---

### Post by Fluxflixflex on 2016-07-19
Any ideas yet ?

Thank you

---

### Post by Fluxflixflex on 2016-07-19
Well,

I understand that no one get much inspiration on this issue, i finally opened my laptop and it turned that was a hardware issue, just dismounting the IO module / putting it back solved the issue...


thank you anyway Ubuntu Community :)

---

### Post by sudodus on 2016-07-19
I saw your problem, but had no clues that could help.

Congratulations, and thanks for sharing your solution :KS

---

### Post by Fluxflixflex on 2016-07-21
Actually nothing to do with the IO module, time to go vback home and issu was the same with my sd card... Then i just saw that my SD car i was using the whole time is a bit broken on the edge (a plastic part is missing) so when I insert into in the SD reader it does not push the little switch.......

Damn i feel so stupid, wasting so much time on this !

Thank you Sudobus :)

---

