---
title: "cannot install jockey on lubuntu"
date: 2013-03-17
forum: Hardware
---

### Post by Luca Borrione on 2013-03-17
I want to try to install a correct nvidia driver for my sistem.
I own an asus s56c ultrabook with Lubuntu 12.10 amd64.

I ran
```
sudo apt-get install jockey-gtk jockey-common
```
Then I cannot see any icon of jockey in the start menu and there is not desktop launcher called jockey in /usr/share/applications.

If I run
```
$ jockey-gtk
The program "jockey-gtk" is currently not installed. You can install it by typing:
sudo apt-get install jockey-gtk
```

but
```
$ sudo apt-get install jockey-gtk
Reading package lists... Done
Building dependency tree
Reading state information... Done
jockey-gtk is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

and
```
$ jockey-text
ERROR:root:Could not find any typelib for AppIndicator3
Additional Drivers
Searching for available drivers...

```

So:
is there any chance to have jockey working on Lubuntu?
Otherwise how can I know which nvidia driver I have to install?

```
$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Device 0153 (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 7 Series/C210 Series Chipset Family Thermal Management Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de3 (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)

```

---

### Post by Frogs Hair on 2013-03-17
On _Ubuntu _12.10  the additional drivers are  located in software sources > additional drivers . I don't know if that is the case with Lubuntu though.

---

### Post by Luca Borrione on 2013-03-17
Thanks for trying!
Jockey is not installed by default on Lubuntu and I cannot find it after having manually installed it.
I found this is a problem Quetzal at
[http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)
where the author advises not to use jockey ayway to automatically install nvidia drivers.

So, being my main aim to install latest nvidia driver on my sistem I opened a new thread on that
[http://ubuntuforums.org/showthread.php?t=2126606](http://ubuntuforums.org/showthread.php?t=2126606)

Thank you

---

### Post by Yellow Pasque on 2013-03-17
You should not install the nvidia driver on a hybrid/Optimus GPU system (the nvidia driver will prevent the Intel graphics from working properly, which is why Additional Drivers doesn't offer it). Instead, remove the nvidia driver:
```
sudo apt-get purge nvidia-current
sudo rm /etc/X11/xorg.conf
```

Then, follow: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

