---
title: "Packard Bell BG-48 with 9.04, log flooding with pcie messages on"
date: 2009-04-23
forum: Hardware
---

### Post by tjerkh on 2009-04-23
Hello,

i have jaunty on a Packard Bell BG-48. My messages log is flooding with these :

Apr 13 15:08:31 packy kernel: [  474.316594] pciehp 0000:00:1c.5:pcie02: Card not present on Slot(37)
Apr 13 15:08:31 packy kernel: [  474.320722] pciehp 0000:00:1c.5:pcie02: Card present on Slot(37)
Apr 13 15:08:31 packy kernel: [  474.344775] pciehp 0000:00:1c.5:pcie02: Card not present on Slot(37)
Apr 13 15:08:31 packy kernel: [  474.348917] pciehp 0000:00:1c.5:pcie02: Card present on Slot(37)
....

Can anybody help me with this? How can i find more? 

Everything seems to work, except no sound, but that is recognized (lspci):

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

Thanx for all input

---

### Post by tyimofej on 2009-10-16
Hi,

I have no solution :confused:, but I would like to assure you, that you are not alone with this problem. I have a BG-35, and it generates exactly the same problems under Ubuntu 9.04 The biggest improvement for me was to reduce the number of the messages a little...
I have added to the /boot/grub/menu.lst the following boot time parameters:
 pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1

Regards,

Gyula

---

### Post by deividblot on 2009-10-31
Hello!! I have the answer. After two night without sleep jkajajk. I am working in the answer. Wait me any days please. 

From Chile!!

pd.: BG48 is a BKN laptop (BKN is greatttt)

---

### Post by reynard on 2009-11-10
I have the same problem. In 9.10 the log is flooding with 'Target link not found' messages. I'm guessing it has something to do with the wireless card and the LED-touch-button to disable it.

I haven't found a solution to date.

Anyone with a solution? Could it have something to do with the asus_laptop driver?

---

### Post by tyimofej on 2009-11-22
Hi,

All my hopes with the new release are gone...:confused: I have installed 9.10, but the problem remains!

deividblot wrote:
"Hello!! I have the answer. After two night without sleep jkajajk. I am working in the answer. Wait me any days please. 
 "
deividblot, cannot wait for your post!!!

---

### Post by boulaskov on 2009-11-24
Hello,
Same problem here with Karmic. Jaunty didn't make me worry so much. Did any of you find a solution?
deividblot, as Obi-Wan Kenobi once has been, You're Our Only Hope!
Hervé

---

### Post by boulaskov on 2009-11-29
Since a few days, after a kernel update, everything seems OK...

---

### Post by tyimofej on 2009-12-03
Hi, 

which kernel do you use?

---

### Post by tyimofej on 2009-12-08
Hi everyone, I have solved the problem.:p
Fact is, that the mainboard in our laptop does not support (or not doing it correctly) thePCIe Native Hotplug. By default, the driver for this feature is compiled into the Ubuntu kernel.
To get rid of these errors, one has to recompile the kernel, and in the config the     **[SIZE=1]CONFIG_HOTPLUG_PCI_PCIE[/SIZE]**

must be swithced off. (=n)

If anyone intrested in further details, please contact me.

Interesting links:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[http://cateee.net/lkddb/web-lkddb/HOTPLUG_PCI_PCIE.html](http://cateee.net/lkddb/web-lkddb/HOTPLUG_PCI_PCIE.html)

---

