---
title: "Please I want Driver and Wireless Graphics Accelerator"
date: 2012-08-09
forum: Hardware
---

### Post by hussiniraq on 2012-08-09
hello..


I me need  driver   


Intel(R) Centrino(R) Wireless-N 1030


and

Radeon (TM) HD 6770M (HP)


me use hp Pavilion dv6-6170se  laotops

---

### Post by hussiniraq on 2012-08-09
up up up up up

---

### Post by ubudog on 2012-08-09
Hi, could you please post the output of:
```
lspci -v
```

---

### Post by hussiniraq on 2012-08-09
> **ubudog said:**
> Hi, could you please post the output of:
```
lspci -v
```
[PHP]Host bridge: Intel Corporation Device 0104 (rev 09)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: c6500000-c74fffff
	Prefetchable memory behind bridge: 00000000a0000000-00000000afffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 6000 [size=64]
	Capabilities: <access denied>

00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at c7504000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at c750a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at c7500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=0c, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: c5500000-c64fffff
	Prefetchable memory behind bridge: 00000000c0400000-00000000c13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=12, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c4500000-c54fffff
	Prefetchable memory behind bridge: 00000000c1400000-00000000c23fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=13, subordinate=18, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c3500000-c44fffff
	Prefetchable memory behind bridge: 00000000c2400000-00000000c33fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=19, subordinate=19, sec-latency=0
	Memory behind bridge: c3400000-c34fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at c7509000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 05)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 35
	I/O ports at 6098 [size=8]
	I/O ports at 60bc [size=4]
	I/O ports at 6090 [size=8]
	I/O ports at 60b8 [size=4]
	I/O ports at 6060 [size=32]
	Memory at c7508000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: medium devsel, IRQ 10
	Memory at c7506000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 6040 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc Device 6740
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: fast devsel, IRQ 3
	Memory at a0000000 (64-bit, prefetchable) [disabled] [size=256M]
	Memory at c6500000 (64-bit, non-prefetchable) [disabled] [size=128K]
	I/O ports at 5000 [disabled] [size=256]
	Expansion ROM at c6520000 [disabled] [size=128K]
	Capabilities: <access denied>

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, fast devsel, latency 0, IRQ 34
	I/O ports at 4000 [size=256]
	Memory at c0404000 (64-bit, prefetchable) [size=4K]
	Memory at c0400000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

0d:00.0 Network controller: Intel Corporation Device 008b (rev 34)
	Subsystem: Intel Corporation Device 5315
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at c4500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

13:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at c3500000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at c2400000 [disabled] [size=64K]
	Capabilities: <access denied>

19:00.0 USB Controller: NEC Corporation Device 0194 (rev 04) (prog-if 30)
	Subsystem: Hewlett-Packard Company Device 3388
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at c3400000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci

[/PHP]

---

### Post by Mark Phelps on 2012-08-09
Sorry, but regarding graphics drivers, HP collaborates with Microsoft in producing their products and they really don't care if those work with Linux.

You have what is known as Hybrid Graphics -- which does NOT work well in Linux.  I have seen older threads where folks were able to disable one of the graphics chips and use only the other one -- but when they upgraded to 12.04, that feature stopped working.

Perhaps someone will come along with a fix that works -- but don't get your hopes up.  

As to wireless, one thing you should do is browse the Networking forum for threads using your wireless chip info.  Someone may have already posted a solution there.

And, as to bumping -- the rule here is once every 24 hours, not once an hour -- as you did.  IF you bump too often, you run the risk of getting your post simply ignored.

---

### Post by hussiniraq on 2012-08-09
hello :(:(

Centrino(R) Wireless-N 1030   need

---

### Post by chili555 on 2012-08-09
It should already be in the kernel. Let's check. Please open a terminal and run and post:```
lsb_release -d
dmesg | grep iwl
rfkill list all
lspci -nn | grep 0280
```Thanks.

---

### Post by hussiniraq on 2012-08-09
> **chili555 said:**
> It should already be in the kernel. Let's check. Please open a terminal and run and post:```
lsb_release -d
dmesg | grep iwl
rfkill list all
lspci -nn | grep 0280
```Thanks.

[IMG]http://im20.gulfup.com/2012-08-10/1344560480451.png[/IMG]

---

### Post by hussiniraq on 2012-08-09
Linux sql-sh 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010

---

### Post by chili555 on 2012-08-09
Your device is covered by the driver iwlwifi in Ubuntu 12.04, but it is too new to be in 10.04. Can you please upgrade?

---

### Post by ubudog on 2012-08-09
> **Mark Phelps said:**
> 
And, as to bumping -- the rule here is once every 24 hours, not once an hour -- as you did.  IF you bump too often, you run the risk of getting your post simply ignored.

Please keep this in mind hussiniraq.

[This]("http://ubuntuforums.org/showpost.php?p=11797600&postcount=6") post may help with your wireless issues.

---

### Post by z3nhakr on 2012-08-09
> **Mark Phelps said:**
> 

You have what is known as Hybrid Graphics -- which does NOT work well in Linux.  I have seen older threads where folks were able to disable one of the graphics chips and use only the other one -- but when they upgraded to 12.04, that feature stopped working.
.

I have a "Hybrid" ati/Intel graphics card (Radeon hd 6400m) and it works great (on precise). To get it working follow this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.6.2C_special_case_for_Intel.2BAC8-ATI_hybrid_graphics]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.6.2C_special_case_for_Intel.2BAC8-ATI_hybrid_graphics")

---

### Post by sffvba[e0rt on 2012-08-09
*Threads **merged**.*  Please do not post more than one thread per issue.


404

---

