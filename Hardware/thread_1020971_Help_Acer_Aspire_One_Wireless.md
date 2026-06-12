---
title: "Help: Acer Aspire One Wireless"
date: 2008-12-24
forum: Hardware
---

### Post by Coder543 on 2008-12-24
Greetings, I have a newly acquired Acer Aspire One, the wireless on it after following the tutorial on the website appears now to be working. However, the wireless module does not seem to want to connect to protected wireless networks. What should I do?

followed:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

search for "wireless broken" to find what I followed.

The AAO is running latest 8.10.

This is the output from lspci -v

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 58480000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 60c0 [size=8]
    Memory at 40000000 (32-bit, prefetchable) [size=256M]
    Memory at 58500000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0
    Memory at 58400000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 58540000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 57300000-583fffff
    Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: 56300000-572fffff
    Prefetchable memory behind bridge: 0000000051000000-00000000520fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 55200000-562fffff
    Prefetchable memory behind bridge: 0000000052100000-00000000530fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 54100000-551fffff
    Prefetchable memory behind bridge: 0000000053100000-00000000540fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 6080 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 6060 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 6040 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 6020 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 58544400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd
    Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-rng, iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 60a0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
    Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: medium devsel, IRQ 11
    I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 219
    I/O ports at 3000 [size=256]
    Memory at 51010000 (64-bit, prefetchable) [size=4K]
    Memory at 51000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 51020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Device e008
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 55200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k_pci
    Kernel modules: ath_pci, ath5k

```

---

### Post by Coder543 on 2008-12-24
*bump* sorry to bump so soon, but using an ethernet cord is not an option that I can accept. I *need* wireless to connect to protected networks if I am going to use Ubuntu on my AA1 at all well.

---

### Post by ericalejandrocasas on 2008-12-26
man im reaaally desperate i might even leave to windows because i tough it  was easy to use this but geez ive followed a few forums and nothing, nothing seems to work with this thing, i love my aa1 but man has it been giving me a headache ive tried this 

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

and a few others

i really dont get this...this is very annoying!

Please HEEELP!!!! ( make a guide idiot proof! pleasse!!)

---

### Post by Coder543 on 2008-12-26
oops, forgot about this thread... Mine works now. Just click this: [Install Linux Backports]("apt:linux-backports-modules-intrepid")
if it asks for a password give it.

---

### Post by ericalejandrocasas on 2008-12-27
Could not find package 'linux-backports-modules-intrepid'.


:'(

---

### Post by Coder543 on 2008-12-27
What version of ubuntu do you have? If you have 8.04 Hardy It *should* work out of the box as I understand it...

---

### Post by albinootje on 2008-12-27
> **ericalejandrocasas said:**
> Could not find package 'linux-backports-modules-intrepid'.


:'(

Please post the output of the following to make it easier for us to help you :
```

lshw -c network
ifconfig -a
route -n
cat /etc/resolv.conf
lsb_release -a
dpkg -l|grep ndis
lsmod|grep -i ath

```
Use .txt file attachments when the output is too long.

---

### Post by ericalejandrocasas on 2008-12-29
heres the output for the terminal codes you guys gave me, thanks for helping!

---

### Post by albinootje on 2008-12-29
> **ericalejandrocasas said:**
> heres the output for the terminal codes you guys gave me, thanks for helping!

Thanks for posting the output.

You seem to be using Ubuntu Jaunty, while in your original posting you mentioned :
> 
The AAO is running latest 8.10.

Have you added more repositories and done upgrades ?
Jaunty is alpha software (Not even beta!), so that means you can run into trouble instantly and every day that you do upgrades!

I recommend installing Ubuntu Hardy / 8.04 on the AAO instead.

---

### Post by Coder543 on 2008-12-29
Intrepid Ibex / 8.10 seems to be doing fine for me, but both are good.

---

### Post by Maddman on 2008-12-29
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

That document takes you through all the steps to figure out what the problem is.

---

### Post by ericalejandrocasas on 2008-12-29
sweet ill give it a try and ill tell you guys whats happened! thanks!!

---

### Post by ericalejandrocasas on 2008-12-30
hey so it worked! but its kinda weird because the network will go off when i restart my lap but hey i cant complain at all!

i did this btw

 	
Re: Help: Acer Aspire One Wireless
oops, forgot about this thread... Mine works now. Just click this: Install Linux Backports
if it asks for a password give it.

---

### Post by ericalejandrocasas on 2008-12-31
so im back to wired haha...sorry for being such a hassle

but i dont know what happened, it dosent seem to detect any drivers now, i opened ''hardware drivers'' and it said no proprietary drivers are in use on this system.
it dosent pick up my access point or anything even with or without the wep key enabled!

---

### Post by Coder543 on 2008-12-31
make sure you didn't flip the hardware switch for the wireless (on the front to the right)

---

### Post by ericalejandrocasas on 2009-01-02
yup already did, but its weird because sometimes it will detect and conecto to wireless networks and I restart my laptop and then nothing

---

