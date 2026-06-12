---
title: "Nvidia Graphics Headache - 14.04.2"
date: 2015-02-20
forum: Hardware
---

### Post by rhys_jones2 on 2015-02-20
Hello all,

I am trying to install Nvidia's graphics drivers on my new system, specs of which will follow. However, no drivers are listed under the addition drivers tab. So, I tried installing manually using

```
sudo apt-get install nvidia-current
```

however it cause ubuntu to load to the login screen wallpaper, the mouse would be active but i wouldnt be able to interact with the system. I have tried editing the xorg.conf file following this guide

[http://askubuntu.com/questions/129322/how-to-install-a-driver-for-an-nvidia-card-not-detected-by-additional-drivers](http://askubuntu.com/questions/129322/how-to-install-a-driver-for-an-nvidia-card-not-detected-by-additional-drivers)

However it loads to a black screen with a small white underscore in the top left, this screen is completely frozen and the only thing i can do is to reset the pc by holding the power button. However, if i press CTRL&ALT&F1 just before it gets to that screen it will load successfully into ubuntu. I have also tried manually installing the nvidia driver from their website however i get the error message "pre-install script failed"

lspci output

```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 860M] (rev a2)
03:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
04:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
```

PC Spec

```
**Chassis & Display**
Optimus Series: 13.3" Glossy QHD+ IPS LED (3200x1800) (Special Offer)
**Processor (CPU)**
Intel® Core&#8482;i7 Quad Core Mobile Processor i7-4710MQ (2.50GHz) 6MB
**Memory (RAM)**
8GB KINGSTON SODIMM DDR3 1600MHz (1 x 8GB)
**Graphics Card**
NVIDIA® GeForce® GTX 860M - 2.0GB DDR5, 640 CUDA Cores - DirectX® 11
**1[SUP]st[/SUP] Hard Disk**
120GB KINGSTON V300 SSD, SATA 6 Gb (450MB/R, 450MB/W)
**Memory Card Reader**
Integrated 6 in 1 Card Reader (SD /Mini SD/ SDHC / SDXC / MMC / RSMMC)
**Thermal Paste**
ARCTIC MX-4 EXTREME THERMAL CONDUCTIVITY COMPOUND 
**Sound Card**
Intel 2 Channel High Definition Audio + MIC/Headphone Jack
**Wireless/Wired Networking**
GIGABIT LAN & KILLER&#8482; 1202 WIRELESS GAMING 802.11N + BLUETOOTH 4.0
**USB Options**
3 x USB 3.0 PORTS + 1 x USB 2.0 PORT AS STANDARD
**Battery**
13.3" Optimus Series 6 Cell Lithium Ion Battery (62.16WH)
```

---

### Post by rhys_jones2 on 2015-02-22
Just an update. The problem was solved by doing this.

```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update


```

---

### Post by garpt01 on 2015-02-22
Thanks.
That will probably help me next week when I will be installing the same card.

---

### Post by rhys_jones2 on 2015-02-22
> **garpt01 said:**
> Thanks.
That will probably help me next week when I will be installing the same card.

Glad it helps, i spent far too long trying to get mine operational

---

### Post by rhys_jones2 on 2015-02-24
garpt01 when you get it installed, let me know if you get an error where it continues to freeze randomly, i have a pain workaround but not a fix.

---

### Post by 1nv1c7u5m4n30 on 2015-04-29
I have this issue after installing the 340.76 Nvidia driver for my Nvidia 760 OC'd edition.
Q9550 @ 2.83Ghz
8gigs 800MHz RAM
Ubuntu 14.04-2
What is the fix and or work around for this issue.  I've searched for almost 2months and cannot find anyone else who's ever had the same problem as me. The system might run with no issue for 24hours or 15min.  I've found nothing giving any kind of reason for this seemingly random lock up of my system.  Temperature, CPU load, Ram, Vram usage, nothing makes any sense.  Any help would be appreciated.
Thanks much in advance!

---

