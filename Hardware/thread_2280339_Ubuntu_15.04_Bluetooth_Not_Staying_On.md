---
title: "Ubuntu 15.04 Bluetooth Not Staying On"
date: 2015-05-29
forum: Hardware
---

### Post by JVP3122 on 2015-05-29
I'm sorry if this has been asked before, but I haven't found anything that pertains to my specific problem.  I have tried turning on bluetooth via the System Settings as can be seen in the attached picture.  Any time I go back out into All Settings and then go back into Bluetooth the bluetooth is turned off.  Here is the result of sudo rfkill list all
```
0: ideapad_wlan: Wireless LAN    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

And here is the result of sudo service bluetooth status:
```
&#9679; bluetooth.service - Bluetooth service   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: inactive (dead)

```

Finally, here is the result of sudo lsusb; uname -a; lsmod | grep bluetooth; dmesg | grep -i firmware
```
Bus 003 Device 002: ID 8087:8000 Intel Corp. Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 03eb:8814 Atmel Corp. 
Bus 001 Device 004: ID 2047:0855 Texas Instruments 
Bus 001 Device 003: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 04f2:b35e Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Linux jeff-Lenovo-IdeaPad-Yoga-11S 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
[    0.210903] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   10.298146] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[   10.300604] RTL8723AU: Firmware Version 33, SubVersion 0, Signature 0x2302
[ 1140.500605] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[ 1147.351080] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[ 1153.986014] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[ 1156.862889] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[ 1159.208420] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[ 1165.838261] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[ 1169.761455] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[ 4549.969870] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[ 4629.589607] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[13483.739687] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[38233.663691] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[38720.652212] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[46372.043996] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[47258.978127] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[56783.364885] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin

```

I tried changing RememberPowered = true in /etc/bluetooth/main.conf but it is already true.  I'm hoping someone can help.

---

### Post by sammiev on 2015-05-30
Hi JVP3122,

Read [this]("http://askubuntu.com/questions/614800/bluetooth-worked-in-ubuntu-15-04-but-not-ubuntu-gnome-15-04") and see if it helps.

---

### Post by JVP3122 on 2015-05-30
> **sammiev said:**
> Hi JVP3122,

Read [this]("http://askubuntu.com/questions/614800/bluetooth-worked-in-ubuntu-15-04-but-not-ubuntu-gnome-15-04") and see if it helps.
Hey sammiev,

I mis-read the solution in that link at first.  Nonetheless I updated my problem to reflect that I tried the method in that link and it did not work.

---

### Post by jeremy31 on 2015-05-30
Try ```
sudo apt-get install git build-essential linux-headers-$(uname -r)
```
```
git clone https://github.com/lwfinger/rtlwifi_new.git
```
```
cd rtlwifi_new
```
```
make
```
```
sudo make install
```
```
cd ~
```
```
git clone https://github.com/lwfinger/rtl8723au_bt.git
```
```
cd rtl8723au_bt
```
```
make
```
```
sudo make install
```

And reboot

The only downside is that the driver will have to be rebuilt after any new kernel is installed but it can be done with

```
cd rtlwifi_new
```
```
make clean
```
```
make
```
```
sudo make install
```
```
cd ~/rtl8723au_bt
```
```
make clean
```
```
make
```
```
sudo make install
```

Then a reboot should have it working once again

---

### Post by JVP3122 on 2015-05-30
When I tried> **jeremy31 said:**
> 
```
cd ~
```
```
git clone https://github.com/lwfinger/rtl8723au_bt.git
```
```
cd rtl8723au_bt
```
```
make
```

I got this error```
make -C /lib/modules/3.19.0-18-generic/build M=/home/jeff/rtl8723au_bt modulesmake[1]: Entering directory '/usr/src/linux-headers-3.19.0-18-generic'
  CC [M]  /home/jeff/rtl8723au_bt/rtk_btusb.o
/home/jeff/rtl8723au_bt/rtk_btusb.c: In function ‘btusb_intr_complete’:
/home/jeff/rtl8723au_bt/rtk_btusb.c:164:3: error: implicit declaration of function ‘hci_recv_fragment’ [-Werror=implicit-function-declaration]
   if (hci_recv_fragment(hdev, HCI_EVENT_PKT,
   ^
cc1: some warnings being treated as errors
scripts/Makefile.build:263: recipe for target '/home/jeff/rtl8723au_bt/rtk_btusb.o' failed
make[2]: *** [/home/jeff/rtl8723au_bt/rtk_btusb.o] Error 1
Makefile:1394: recipe for target '_module_/home/jeff/rtl8723au_bt' failed
make[1]: *** [_module_/home/jeff/rtl8723au_bt] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-18-generic'
Makefile:15: recipe for target 'all' failed
make: *** [all] Error 2
```

---

### Post by jeremy31 on 2015-05-30
```
rm -r rtl8723au_bt
```
```
git clone -b troy https://github.com/lwfinger/rtl8723au_bt.git
```
```
cd rtl8723au_bt
```
```
make
```
```
sudo make install
```

Reboot

---

### Post by JVP3122 on 2015-05-30
> **jeremy31 said:**
> ```
rm -r rtl8723au_bt
```
```
git clone -b troy https://github.com/lwfinger/rtl8723au_bt.git
```
```
cd rtl8723au_bt
```
```
make
```
```
sudo make install
```

Reboot
Worked like a charm.  Thanks for the help.

---

