---
title: "Acer aspire 1640z linux help!"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by xardas on 2006-10-22
I've just bought a new Acer laptop and installed ubuntu on it. I`ve been using ubuntu on my desktop pc for a couple of months. So anyway I would just like to know where I could get all the different drivers to make it run smoothly. The CD that came with the laptop only contained the drivers for windows. And there is also no sound. How can I get some sound? The touchpad is also working a little wierd. So any link for touchpad and video drivers?](*,)

---

### Post by xardas on 2006-10-22
Also the modem is not recognized. So I cant use internet. What to do? It is an 'HDAUDIO Soft Data Fax Modem with SmartCP'. Thats what windows tells me.

---

### Post by xardas on 2006-10-22
Ok I did the lspci command and got this output:

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

My modem is not mentioned there. Its something called 'High definition audio Modem'. How do get Ubuntu to recognize it?

---

### Post by xardas on 2006-10-23
Its a high definition audio modem. Anyone know where I can find its drivers?

---

### Post by xardas on 2006-10-23
Ok I've solved the sound problem after reading up on a forum and downloading the latest alsa drivers. That was easy. So anyone help with the modem?

---

