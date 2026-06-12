---
title: "wireless problem"
date: 2011-12-08
forum: Hardware
---

### Post by frostychill on 2011-12-08
I in stalled ubuntu 10.11 on my dell latitude yesterday. i can't connect to wifi because it says i need a firmware update. how do i do that?

---

### Post by TBABill on 2011-12-08
First we need to known which wireless device the computer has. Can you open a terminal and type the following, the paste the results back here so we can help further: ```
lspci
``` That's LSPCI in lowercase...lists your PCI devices. If it's USB, instead use LSUSB in lowercase.

---

### Post by frostychill on 2011-12-08
im kind of new to laptops. how do i do that?

---

### Post by TBABill on 2011-12-08
Just open the application called Terminal, type in that single code (lspci) and when it provides an output, highlight it, right click and select "copy", then paste it back here on the forum so we can see it.

---

### Post by frostychill on 2011-12-08
i don't think i have it. where can i get it
:confused:

---

### Post by TBABill on 2011-12-09
Terminal is an application included with every Linux distro. if you're in Ubuntu 11.10, go to where you can see all applications and find it alphabetically or in the search bar just type terminal.

---

### Post by frostychill on 2011-12-09
Oh. i was looking on windows xp. thanks. ill post the results

---

### Post by frostychill on 2011-12-09
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4306 802.11a/b/g (rev 03)
jonathan@ubuntu:~$

---

### Post by TBABill on 2011-12-10
In a terminal, just ```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Just paste that into a terminal and hit enter. Once it finishes, then ```
sudo modprobe b43
```Wait a few moments then connect to your network.

---

