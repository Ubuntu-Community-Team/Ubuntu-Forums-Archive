---
title: "[SOLVED] wifi driver problem rtl8723? Bluetooth works, wifi unrecogmoized."
date: 2018-10-12
forum: Hardware
---

### Post by dt3 on 2018-10-12
Hello, i recently bought 15' HP laptop for my mother. It is model[COLOR=#1D2129][FONT=Helvetica] 15-bs151nw. Machine was sold without the system (with free dos) - it was good for me, since intended use is Linux Laptop.

Everything works fine on Ubuntu 18.04.1 except integrated bluetooth-wifi card. I tried resolving problem on my own, but i got lost. Not sure what to do next. 
I got Bluetoth work, but cant get WiFi working.

output of lspci is: 
[/FONT][/COLOR]```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Processor Thermal Subsystem (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.5 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #6 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
0d:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device d723



```

[COLOR=#1D2129][FONT=Helvetica]Output of lsusb:
[/FONT][/COLOR]```
Bus 001 Device 002: ID 8087:8001 Intel Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 05c8:0233 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 0bda:b009 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```[COLOR=#1D2129][FONT=Helvetica]
[/FONT][/COLOR]It looks that troublemaker is this device:
```
Bus 002 Device 002: ID 0bda:b009 Realtek Semiconductor Corp.
```

What i've tried already:
[LIST]
[*]I tried to get driver from [https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi) - unfortunatelly no release list for this version of Ubuntu in his ppa
[*]I got driver/kernel module from lwfinger github
[*]I disabled secure boot, and loaded other rtl module into kernel
[/LIST]
Honestly i'm loosing track of what i've already tried and really got lost. Thats why i paste here also output from bash history
```
$ history | grep rtl    5  sudo apt search rtl8723
    7  sudo apt search rtl8723
    9  sudo apt-get ppa:hanipouspilot/rtlwifi
   10  sudo add-apt-repository ppa:hanipouspilot/rtlwifi
   12  sudo add-apt-repository ppa:hanipouspilot/rtlwifi
   13  sudo apt-get install rtlwifi-new-dkms linux-firmware
   15  sudo dkms add ./rtl8723bu
   16  git clone https://github.com/lwfinger/rtl8723bu
   17  sudo dkms add ./rtl8723bu
   18  source rtl8723bu/dkms.conf
   19  sudo dkms add ./rtl8723bu source rtl8723bu/dkms.conf
   20  sudo dkms install rtl8723bu/$PACKAGE_VERSION
   21  sudo tee /etc/modprobe.d/blacklist-rtl8xxxu.conf <<< "blacklist rtl8xxxu"
   31  dmesg | grep rtl

```

At the moment i have to use either wired conecction or use Bluetooth teethernig to connect this laptop to wifi on slightly strange way: I conect mobile phone to Wifi, than use it as a hotspot sharing internet via Bluetooth. I'd like to get wifi working on this laptop itself.

Can You, please suggest me what should i do next, to make this Wifi work

---

### Post by jeremy31 on 2018-10-12
With internet connection, run the following commands in terminal, one line at a time
```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```

Reboot

---

### Post by dt3 on 2018-10-12
Thank You jeremy31
It worked :)

So i guess - my mistake was using wrong git / ppa ? 
What could i did better?

---

### Post by dannydcrespo on 2018-10-14
I was facing this issue from the last night finally able to solve it. Thanks

---

