---
title: "Latitude D630 network card problems"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by daehenoc on 2008-04-09
Hi all,

I'm supporting a small business and the Director's laptop, a Latitude D630 running Ubuntu 7.10 and we've got an intermittent problem, sometimes the wireless LAN appears to "go away" in their words, I haven't gotten my hands on the laptop when it's happened (such is the life of a Director...) but it seems like the module for the wireless card locks up or is unloaded or something.

output of lspci:
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Rebooting will fix this problem, but sometimes the laptop locks up totally when attempting this reboot and they need to do a hard power off of the device.

Has anyone else had any kind of problems like this?

Thanks,
Greg

---

### Post by nightcrawler27 on 2008-04-11
I take it the card is the Intel Pro Wireless 3945 at the bottom of your lspci output? can you do an "lsmod | grep ipw" and post the output? I'm looking to see what driver you are using for the wireless card. 

The other thing is in the Dell Latitude BIOS settings, there is an option for enabling the fn-f2 key to control the activation/deactivation of the radio. Try deactivating the key combination setting in the bios.

I find sometimes I fat-finger the shift button and the number 2 (makes the @ sign, a very common thing to type). Since the F2 is above the "2" key and the "Fn" key is just below the left "shift" key, it is very easy to disable the radio without knowing it! My Latitude D810 has this key combination, I believe the D630 has it as well.


nightcrawler27

---

### Post by daehenoc on 2008-04-29
Believe it or not, this is the first time I've gotten my hands back on this laptop, the life of a Director is pretty busy...

Anyway, yes, this laptop does have the 3945 chipset and here is the output of lsmod: 
```
$ lsmod | grep ipw
ipw3945               119840  1 
ieee80211              35656  1 ipw3945
```

Thanks for the tip on the wireless switch, I've disabled it in the BIOS.

The owner hasn't had any further wireless dropouts, but the laptop still locks up irregularly.  I have the laptop for this week and I'm using it until Thursday with Gutsy on it, if it hasn't crashed by Thursday, I am upgrading it to Hardy.  (Apparently this will fix the issue of no sound as well.)

---

### Post by nightcrawler27 on 2008-05-01
Sounds like a plan...I am using Hardy and it is great. Maybe it will help. Not sure what could cause the "lockups". I have never had my system lock up on me while running Linux.


nightcrawler27

---

### Post by daehenoc on 2008-05-02
I upgraded this laptop to Hardy on Thursday night (two days ago) and I haven't had any problems with the wireless since :)

Here's the relevant output from lsmod:
```
$ lsmod | grep iwl3945
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
```

I have had a one WEIRD problem which I have started a new thread about here: [http://ubuntuforums.org/showthread.php?t=779551](http://ubuntuforums.org/showthread.php?t=779551)

Apart from that it's fine.

---

