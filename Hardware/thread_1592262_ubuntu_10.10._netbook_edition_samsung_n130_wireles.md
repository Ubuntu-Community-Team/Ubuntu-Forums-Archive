---
title: "ubuntu 10.10. netbook edition samsung n130 wireless does not work"
date: 2010-10-10
forum: Hardware
---

### Post by gabak on 2010-10-10
hi
i see i m the first one to have problem with the newest version of ubuntu netbook.
i had ubuntu 10.04 working just fine on this netbook and today i format the hdd and i install a fresh ubuntu and this version seem to be working fine everything but except wifi.
i mean i see all the signals but i cant connecto to mine.
it has wep encryption.
i tried my neightbord wifi that i know the password and nothing.
i have other netbook asus 1201t and i install ubuntu 10.10 and wifi and everything works just fine.

---

### Post by kevinwincott on 2010-10-12
im having exactly the same issue, having checked the logs there are lots of kernel errors.......

---

### Post by ally1708 on 2010-10-12
I am also having problems with the wifi, on the other half's N130. When I Installed 10.10 the wireless worked no problem, I switched it on today and it can't connect to the router. No other wireless device in the house is having problems. This includes my laptop running 10.10 and an acer revo running 10.04

---

### Post by gabak on 2010-10-12
hi
i got fixed by itself.
maybe after few updates it started working just fine

---

### Post by ally1708 on 2010-10-13
Just updated using an ethernet cable, when done I tried the wireless again and it made no difference.

---

### Post by roadrash on 2010-10-13
I have just installed 10.10 maverick meerkat to A samsung N130 & I had the wireless working from the live cd so installed it.  The wireless worked on the first boot and i was able to enter the key wpa key and get net access.  However, the next time I booted it up after a cold start the wireless would not connect anymore and i could not see any activity from the lights on the router. can anyone help with this.

here is the output of lspci -v

> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at f0200000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, fast devsel, latency 0
    Memory at f0080000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0100000-f01fffff
    Prefetchable memory behind bridge: 0000000040000000-00000000401fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c05d
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 40200000-405fffff
    Prefetchable memory behind bridge: 00000000f0500000-00000000f05fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c05d
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0444000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: [50] Subsystem: Samsung Electronics Co Ltd Device c05d

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1810 [size=16]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Samsung Electronics Co Ltd Device c05d
    Flags: medium devsel, IRQ 5
    I/O ports at 18a0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
    Subsystem: Askey Computer Corp. Device 7160
    Flags: bus master, fast devsel, latency 0, IRQ 16
    I/O ports at 2000 [size=256]
    Memory at f0100000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 34-e4-62-fe-ff-b6-26-00
    Kernel driver in use: rtl819xE
    Kernel modules: r8192se_pci, r8192e_pci

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Samsung Electronics Co Ltd Device c04d
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at 3000 [size=256]
    Memory at f0510000 (64-bit, prefetchable) [size=4K]
    Memory at f0500000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at f0520000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=2 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-00-00-00-00
    Kernel driver in use: r8169
    Kernel modules: r8169


---

### Post by commandergc on 2010-10-16
Having the same issue with my N130 too. Live CD worked ok, first boot after install the wireless worked but after that nothing. here is the output of dmesg while trying to connect. The wireless card is an RTL8192E.

```
[ 1786.985794] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 1786.985813] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0,26
[ 1789.489081] Linking with NSSID,channel:6, qos:0, myHT:1, networkHT:0
[ 1789.489103] ===>ieee80211_associate_procedure_wq(), chan:6
[ 1789.504829] =================>ieee80211_authentication_req():auth->algorithm is 0
[ 1789.504854] rtl819xE:No more TX desc@6, ring->idx = 0,idx = 0,26
[ 1792.009115] Linking with SSID,channel:6, qos:0, myHT:1, networkHT:0
[ 1792.009137] ===>ieee80211_associate_procedure_wq(), chan:6

```
--EDIT
Just updated the kernel and the wireless now works!

---

### Post by haegar_the_root on 2010-10-16
@commandergc:

Which kernel version are you using?
Is it a standard version or a special N130 version?
Any freezes?

Thank you for a short reply.

---

### Post by commandergc on 2010-10-16
its 2.6.35-22.34 Standard version from ubuntu repo the update appeared this morning.

No stability issues so far.

---

### Post by TBABill on 2010-10-16
This seems to be a widespread problem across many different wireless adapters. I did a fresh install to 10.10 and could see networks but not connect. Wired was fine. I searched all over the forums and the Internet, but found no fix. I just reinstalled 10.04 and all is well again.

---

### Post by commandergc on 2010-10-17
well spoke to soon it's stopped working again! getting the same errors as my post post above.

---

### Post by commandergc on 2010-10-17
May have found the solution. Found this driver for the RTL8192E with an install script by [dirk hoeschen]("http://www.dirk-hoeschen.de") You will need Build Essentials and the kernel headers installed for this to work.

```

sudo apt-get install build-essential
tar -xpf rtl819Xe.tar.gz
cd rtl819Xe
sudo ./install.sh

```

sofar so good several reboots and cold starts and it's still working!

---

### Post by kin242 on 2010-10-19
sudo apt-get install build-essential kernel-headers-$(uname -r)

- this doesnt work for me- I get an error- unable to locate package...

---

### Post by commandergc on 2010-10-19
try without the "kernel-headers-$(uname -r)" part. Ubuntu installs them by default anyway.

---

### Post by haegar_the_root on 2010-10-19
I wonder why the RTL8192E is not running out of the box, because it's part of the kernel tree of Linus Torvalds:
[linux/kernel/git/torvalds/linux-2.6.git] / drivers / staging / rtl8192e /
(as mentioned by Dirk Hoeschen).

With older ubuntu netbook editions the card works perfectly.

---

### Post by commandergc on 2010-10-19
I'm starting to think that it's not the driver it self but maybe something to with the firmware. I reinstalled Ubuntu ran Dirk's installer then downloaded the updated kernel, this replaced the driver that was installed but not the firmware. The card still works although is a bit slow to connect. The problem needs to be looked at in more detail, something i can not do as my knowledge is limited.

---

### Post by ally1708 on 2010-10-23
Thank you [commandergc]("http://ubuntuforums.org/member.php?u=104754") I managed to get the wireless going with that script.

I do have one question though, to use the script as it is where do you have to have the driver when you extract it?

I had to change it from this:
tar -xpf rtl819Xe.tar.gz

to this:
tar -xpf /home/username/Downloads/rtl819Xe.tar.gz


I'm still quite new to Ubuntu and although I got it to work I just couldn't figure out where the driver should have been to just run the script.

Cheers
Ally

---

### Post by jcr1 on 2010-10-25
> **commandergc said:**
> May have found the solution. Found this driver for the RTL8192E with an install script by [dirk hoeschen]("http://www.dirk-hoeschen.de") You will need Build Essentials and the kernel headers installed for this to work.

```

sudo apt-get install build-essential
tar -xpf rtl819Xe.tar.gz
cd rtl819Xe
sudo ./install.sh

```

sofar so good several reboots and cold starts and it's still working!

Thank you! Got it working for me...

Was very frustrated as my WiFi has worked out of the box for at least the last 2 or 3 releases. Seems weird to have gone back a step again...

Thanks again.

---

### Post by dafrostyone on 2010-10-31
> **commandergc said:**
> May have found the solution. Found this driver for the RTL8192E with an install script by [dirk hoeschen]("http://www.dirk-hoeschen.de") You will need Build Essentials and the kernel headers installed for this to work.

```

sudo apt-get install build-essential
tar -xpf rtl819Xe.tar.gz
cd rtl819Xe
sudo ./install.sh

```

sofar so good several reboots and cold starts and it's still working!

```
Installing module and rebuilding dependencies...
Removing r8192e_pci and  r8192se_pci...
ERROR: Module r8192e_pci does not exist in /proc/modules
ERROR: Module r8192se_pci does not exist in /proc/modules
```

My wireless won't connect until i run this script. After a reboot the wireless won't connect again, meaning i must run this script every time i start my laptop. Does anybody know of a more permanent fix?

I also attempted a fix posted elsewhere on here which gave some drivers to download and instructions on how to use them, however i'm getting this error and am unable to find the thread in which they were suggested...

```
N130:~/Downloads/rtl8192e_linux_2.6.0014.0401.2010$ sudo ./wlan0down
ERROR: Module r8192e_pci does not exist in /proc/modules
N130:~/Downloads/rtl8192e_linux_2.6.0014.0401.2010$ sudo ./wlan0upinsmod: error inserting 'r8192e_pci.ko': -1 No such device
N130:~/Downloads/rtl8192e_linux_2.6.0014.0401.2010$ 
```

---

### Post by liamgh on 2010-11-11
I recently got a Samsung NB30 which also has a RTL8192E wireless card and had lots of problems with the built in driver in Ubuntu 10.10's kernel. In the end I found a way to make it more reliable was to use the driver in the samsung-wireless package from the PPA for Samsung Netbooks at [https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa). I had to add this entry to /etc/modprobe.d/blacklist.conf to stop the default driver from loading:
**blacklist r8192e_pci **
After that it has been much more reliable so far.

I wrote a blog post with details on this and other steps I took to install Ubuntu on the NB30 and it is here:
[http://www.greenhughes.com/content/installing-ubuntu-1010-samsung-nb30-touchscreen-netbook](http://www.greenhughes.com/content/installing-ubuntu-1010-samsung-nb30-touchscreen-netbook)

---

### Post by vadaim on 2010-12-03
[#20, liamgh's solution]("http://ubuntuforums.org/showpost.php?p=10104853&postcount=20") worked best for me on N130.

---

### Post by wshatner on 2011-01-16
If anyone can help me through how to implement Liam's solution I'd really appreciate it (newbie to Ubuntu and Linux and using the terminal...

Thanks!

---

### Post by JibXB on 2011-02-27
Thanks, LiamGH!  Same situation, Samaung N130 & Maverick Wi-Fi problems.  

I tried every solution in these threads before trying yours.  The solution you posted was effective, but I must say that some of us people who are newer to Linux/Ubuntu may find that it could be better detailed.  I suppose that people who are more accustomed to coding, working computer software (I'm more of a hardware guy), or general engineering minded people may take to the descriptions pretty easily.  I spent hours traversing several different websites, and I think I ended up doing some things that I really didn't need to out of confusion.  

All in all, though, your solution was the only one amongst this particular thread that was effective in my situation.  I thank you for helping to guide me in the right direction!

---

### Post by R3P71L3 on 2011-05-25
Do I need to do all these steps in order?  I got inpatient and jumped ahead to running install.sh but was told the file didn't exist.  I double-checked that the Konsole was in the directory that had the file and ran -ls to make sure it was there, but was still told it didn't exist.  Guess I'll try the whole thing tomorrow (don't have a wired connection or I'd have done it already).

---

