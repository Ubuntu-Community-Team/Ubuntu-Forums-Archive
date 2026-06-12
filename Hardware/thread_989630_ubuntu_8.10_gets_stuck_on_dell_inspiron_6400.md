---
title: "ubuntu 8.10 gets stuck on dell inspiron 6400"
date: 2008-11-21
forum: Hardware
---

### Post by spandanj on 2008-11-21
**Problem**: A fresh install of ubuntu 8.10 gets stuck within 20-30 minutes since boot. This has already happened 4 times in last 2 hours, ie. my first 2 hours since a brand new installation.

**Clue**: when it gets stuck, the numlock, capslock, and sometimes even wifi light on my laptop starts flickering.

**computer**: dell inspiron 6400

**method of installation: **

--> pop in 8.10 cd-->manual partition-->delete 8.04 partition-->install in new free space
--> system updated after fresh installed. installed smplayer and ATI driver as requested by ubuntu system

**Prior history:** 8.04 worked perfectly for 6 months

_**[COLOR="MediumTurquoise"]Please HELP ASAP[/COLOR]**_. I can't use my laptop.....

thank you.

---

### Post by spandanj on 2008-11-21
I dont know what the problem is, 

but does this help?

dmesg | grep iwl3945
[   14.224505] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.224510] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   14.224649] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.224666] iwl3945 0000:0b:00.0: setting latency timer to 64
[   14.224693] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   14.468915] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.865591] iwl3945 0000:0b:00.0: PCI INT A disabled
[   26.792168] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.792331] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   63.980884] iwl3945 0000:0b:00.0: PCI INT A disabled
[ 1073.566607] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1073.566792] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 1272.703613] iwl3945 0000:0b:00.0: PCI INT A disabled
[ 1349.876338] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1349.876525] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 1436.288112] iwl3945 0000:0b:00.0: PCI INT A disabled
[ 1525.533302] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1525.533489] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 1688.442156] iwl3945 0000:0b:00.0: PCI INT A disabled
[ 1844.383988] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1844.384176] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)

dmesg | grep iwl
[   14.224505] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.224510] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   14.224649] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.224666] iwl3945 0000:0b:00.0: setting latency timer to 64
[   14.224693] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   14.468915] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.478769] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   14.865591] iwl3945 0000:0b:00.0: PCI INT A disabled
[   26.792168] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.792331] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   26.792781] firmware: requesting iwlwifi-3945-1.ucode
[   26.907688] Registered led device: iwl-phy0:radio
[   26.907853] Registered led device: iwl-phy0:assoc
[   26.908020] Registered led device: iwl-phy0:RX
[   26.908162] Registered led device: iwl-phy0:TX
[   63.980884] iwl3945 0000:0b:00.0: PCI INT A disabled
[ 1073.566607] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1073.566792] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 1073.612725] Registered led device: iwl-phy0:radio
[ 1073.613364] Registered led device: iwl-phy0:assoc
[ 1073.614685] Registered led device: iwl-phy0:RX
[ 1073.614793] Registered led device: iwl-phy0:TX
[ 1272.703613] iwl3945 0000:0b:00.0: PCI INT A disabled
[ 1349.876338] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1349.876525] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 1349.922383] Registered led device: iwl-phy0:radio
[ 1349.922417] Registered led device: iwl-phy0:assoc
[ 1349.922479] Registered led device: iwl-phy0:RX
[ 1349.922503] Registered led device: iwl-phy0:TX
[ 1436.288112] iwl3945 0000:0b:00.0: PCI INT A disabled
[ 1525.533302] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1525.533489] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 1525.579086] Registered led device: iwl-phy0:radio
[ 1525.580203] Registered led device: iwl-phy0:assoc
[ 1525.581146] Registered led device: iwl-phy0:RX
[ 1525.583728] Registered led device: iwl-phy0:TX
[ 1688.442156] iwl3945 0000:0b:00.0: PCI INT A disabled
[ 1844.383988] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1844.384176] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 1844.430435] Registered led device: iwl-phy0:radio
[ 1844.430541] Registered led device: iwl-phy0:assoc
[ 1844.430582] Registered led device: iwl-phy0:RX
[ 1844.430622] Registered led device: iwl-phy0:TX

---

### Post by spandanj on 2008-11-22
ok, so no help yet....

however I noticed something peculiar...

From [http://www.intellinuxwireless.org/?p=iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi)
** Using kernels 2.6.24 and up**
These kernels have the iwlwifi driver included and the released drivers (available from this site under download page) do not work with these kernels. If you want to run the latest (or very close to it) development code with your kernel then you should use the compat-wireless project that retrieves the latest driver development code from the upstream repository. We do push our changes to this repository very frequently. 
--------------------
does this mean that the problem lies with using iwl3945 instead of iwlwifi???

I have no clue what I am talking about. I am shooting in the dark here. I don't even know if the problem is related to the wireless network. However, It is VERY likely because it hasn't frozen on lan...............!

I don't understand. If the driver is the problem....incompatible with kernel, DON't release the kernel in update knowing the "unupdated" drivers won't work. or make sure you KNOW that they will work before releasing a new kernel...Will there ever be a time things don't go breaking in linux....like this.

However, I still need help on what to do here. I do need my wireless internet to work. so, any help is welcome. my kernel is 2.6.27.7

---

### Post by Frem on 2008-11-22
Does it crash after that period of time regardless of use? If so, you might be able to catch a glimpse of the kernel panic error message by hitting Ctrl + Alt + F1 and waiting for the system to go down.

I believe there are also programs that can capture kernel panics. Google might help here.

---

### Post by spandanj on 2008-11-22
I didn't check without activity.

However, it didn't crash for 10 hours when I disabled the wireless.

But, before that, it crashed within first 10 mins of boot if I had wireless enabled.

So, I guess the problem was somewhere with wireless. Sadly, when I re boot the computer it doesn't tell/prompt me that it had crashed. it'd be kinda nice to have a prompt on the next restart saying improper shut down, and giving relevant information that may be useful to solve the prob. 

FINALLY, i just installed 8.04 instead ...back. I am really disappointed in ubuntu that an upgrade would could such a serious 'breakage'. I really don't believe in ubuntu to be the common, mainstream distribution for common/new users. will try suse.

---

### Post by Regre on 2009-02-17
Hi, I have the same problem!!! Did u manage to solve the problem or did you just switch to 8.4 and never tried 8.10 again?

Thanx

---

### Post by spandanj on 2009-02-17
Regre,

I never managed to solve the problem. I quickly switched back to 8.04. I did'nt have the time solve it.


8.04 works fine.

---

### Post by bagseed on 2009-02-18
Same issues ....I just upgrade from 8.04 to .10 and starting having this problem. Now I am forced to look at the possibility of formating and reloading hardy. 

System: Compaq nx7400 
OS:xbuntu: 8.10 64bit
kernel: 2.6.27-11-generic #1 SMP

After a few secs or minutes upon a successful connection to a WPA Enterprise network the system just locks up requiring a power cycle. The system seems to only do it, again, after a successful wifi  connection. I have to use the lan for now :( 


$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


dmesg |grep iwl3945
[   14.717931] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   14.717935] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   14.718016] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.718031] iwl3945 0000:10:00.0: setting latency timer to 64
[   14.718054] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   14.780658] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.276587] iwl3945 0000:10:00.0: PCI INT A disabled
[   33.654664] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   33.654816] iwl3945 0000:10:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   33.745386] iwl3945: Radio disabled by HW RF Kill switch
[   33.745482] iwl3945 0000:10:00.0: PCI INT A disabled
[   33.758288] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   33.758443] iwl3945 0000:10:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   33.758717] iwl3945: Radio disabled by HW RF Kill switch
[   33.758783] iwl3945 0000:10:00.0: PCI INT A disabled
[ 2033.153317] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2033.153487] iwl3945 0000:10:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)


 dmesg |grep iwl
[   17.129719] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   17.129723] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   17.185295] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.185310] iwl3945 0000:10:00.0: setting latency timer to 64
[   17.185327] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   17.251791] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   17.253193] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.438797] iwl3945 0000:10:00.0: PCI INT A disabled
[   36.313176] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   36.313346] iwl3945 0000:10:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   36.313648] firmware: requesting iwlwifi-3945-1.ucode
[   36.446752] Registered led device: iwl-phy0:radio
[   36.447154] Registered led device: iwl-phy0:assoc
[   36.447418] Registered led device: iwl-phy0:RX
[   36.447673] Registered led device: iwl-phy0:TX
[   80.454806] iwl3945: Radio Frequency Kill Switch is On:
[   80.942014] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   80.945043] iwl3945: MAC is in deep sleep!
[   80.991719] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   80.995678] iwl3945: MAC is in deep sleep!
[   81.051293] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   81.055287] iwl3945: MAC is in deep sleep!
[   81.214365] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   81.230740] iwl3945 0000:10:00.0: PCI INT A disabled
[15974.634431] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[15974.634597] iwl3945 0000:10:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[15974.706411] Registered led device: iwl-phy0:radio
[15974.706495] Registered led device: iwl-phy0:assoc
[15974.706527] Registered led device: iwl-phy0:RX
[15974.706556] Registered led device: iwl-phy0:TX
[15994.328101] iwl3945 0000:10:00.0: PCI INT A disabled

---

### Post by Fahim-Uddin on 2009-03-06
i'm having similar problem ... ubuntu 8.10 not detecting my wifi ... i'm using Dell INSPIRON 6400 .....

---

### Post by Regre on 2009-03-20
I don't know why.... but since Wednesday, my laptop didn't crased because of the wifi... Usually after 30 minutes, it crashes but now I have been using it for several hour in a row with no problem..

plus it's seems to have fixed my connection problem to the school vpn. ( usually it takes 20 attemps to connect and now it only took me 2.... )

I guess they fixed the problem some how... 

Regre

---

### Post by Regre on 2009-03-23
yeah well just forget what i said last week.... the problem came back....


Regre

---

### Post by Regre on 2009-03-31
I think  Leann Ogasawara might have solve our problem 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349915](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349915)


"I installed via synaptic
linux-backports-modules-intrepid 2.6.27.11.14 ( it will ask you to install the 2 other programs)
linux-backports-modules-intrepid-generic 2.6.27.11.14
linux-backports-modules-intrepid-2.6.27.11-generic 2.6.27.11.12 "

and my computer didn't crashed for 2 hours non-stop while using the wifi. i'll keep you posted if the problem reappear

 thanks a lot to Leann Ogasawara!!!!!!

---

