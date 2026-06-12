---
title: "Help With Laptop Drivers!!!!!!"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by bloodhacker2 on 2008-02-05
Hey guys,,

hey i am trying to get my drivers for my video, sound, chipset, and most of all my wireless drivers to work.
her is what kind of computer i have and a list of drivers i have install for winxp, i am dule booting winxp and Ubuntu and the list or drivers are the ones i installed on winxp.....

[http://www.walmart.com/catalog/product.do?product_id=5663691](http://www.walmart.com/catalog/product.do?product_id=5663691)

Atheros AR5007EG Wireless Network Adapter

Chipset Driver Intel 8.0.0.1009

VGA Driver Intel 6.14.10.4543

Audio Driver 5.10.0.5273

i am looking on how to install the on Ubuntu, or what kind of commands do i need to run to get the driver for this computer.....

---

### Post by tizza10 on 2008-02-06
You should not need to use drivers for your hardware, most are supported by the distribution. Are you having particular problems with the hardware? Your wireless card is different, try [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828) or [www.google.com/linux](www.google.com/linux)

---

### Post by Yellow Pasque on 2008-02-06
That doesn't really give us a good idea of what hardware you have.
Go to the terminal in Ubuntu (under Applications->Accessories) and run:
```
lspci
```
Post the output here.

---

### Post by Daelyn on 2008-02-06
What make and model is it?

Quite a lot of "laptop specific" how-to's here and there in this forum :)

---

### Post by ningall on 2008-02-06
I have the same wireless chipset and to get it to work i used madwifi

. Open you terminal

2. Get this version of madwifi:

    wget -c [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

3. Untar the downloaded package:

    tar xvf madwifi-ng-r2756+ar5007.tar.gz

4. Get inside the unpacked directory:

    cd madwifi-ng-r2756+ar5007

5. If you haven’t compiled anything from source before on your linux then you propably need the build essential package:

    sudo apt-get update && sudo aptitude install build-essential

6. Now you can build your madwifi and install the modules:
make

    sudo make install
    sudo modprobe ath_pci
    sudo modprobe wlan_scan_sta

The last 2 commands can cause some complications on some systems. If they do check your System >> Administration >> Restricted Drivers Manager and disable atheros here. Then try again.

7. Now restart your computer and you should be able to see any aviable networks in your Network Manager.

That is the guide i used to get it working

---

### Post by bloodhacker2 on 2008-02-07
> **Temüjin said:**
> That doesn't really give us a good idea of what hardware you have.
Go to the terminal in Ubuntu (under Applications->Accessories) and run:
```
lspci
```
Post the output here.

hear is the output...

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

---

