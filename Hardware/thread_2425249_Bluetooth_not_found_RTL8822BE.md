---
title: "Bluetooth not found RTL8822BE"
date: 2019-08-22
forum: Hardware
---

### Post by ariel16 on 2019-08-22
Hi, I just installed Ubuntu 19.04 on my HP 250 G7. It has a RTL8822BE wireless/bluetooth combo chip. Wifi works fine but bluetooth does not work (see screenshot).

```
$ lspci | grep RTL8822BE
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter


```

```
$ lsmod | grep bluetooth
bluetooth             557056  0
ecdh_generic           28672  1 bluetooth


```

```
$ hcitool scan
Device is not available: No such device


```

Thanks in advance!

---

### Post by #&amp;thj^% on 2019-08-22
Give this a shot to help us here:
```
systemctl status bluetooth

```
Post back the return in code tags. :)

---

### Post by jeremy31 on 2019-08-22
Also post results for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by ariel16 on 2019-08-23
```
$ systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: inactive (dead)
Condition: start condition failed at Fri 2019-08-23 10:12:00 CEST; 1h 30min left
           &#9492;&#9472; ConditionPathIsDirectory=/sys/class/bluetooth was not met
     Docs: man:bluetoothd(8)

Aug 23 10:12:00 Latnook-HP-250-G7-Notebook-PC systemd[1]: Condition check result
lines 1-8/8 (END)


```

```
$ lsusb; dmesg | egrep -i 'blue|firm'
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 04f2:b67f Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.278942] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    3.377518] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[    3.525069] [Firmware Bug]: ACPI(PXSX) defines _DOD but not _DOS

```

---

### Post by #&amp;thj^% on 2019-08-24
Load the generic bluetooth driver, if not already loaded by typing the following in your terminal:
```

sudo modprobe btusb
```

Use systemctl to start the Bluetooth service
```

sudo systemctl start bluetooth
```
Any Luck?
If not show us this please:
```
**_rfkill list_**
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

---

### Post by ariel16 on 2019-08-24
> **1fallen said:**
> Load the generic bluetooth driver, if not already loaded by typing the following in your terminal:
```

sudo modprobe btusb
```

Use systemctl to start the Bluetooth service
```

sudo systemctl start bluetooth
```
Any Luck?
If not show us this please:
```
**_rfkill list_**
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Still doesn't work

```
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by #&amp;thj^% on 2019-08-24
By chance are you also dual booting with Windows? And if so did it work on windows?
rfkill shows no bluetooth so try:
```
sudo rfkill unblock bluetooth
```
now show us:
```
sudo service bluetooth start
```

---

### Post by ariel16 on 2019-08-24
> **1fallen said:**
> By chance are you also dual booting with Windows? And if so did it work on windows?
rfkill shows no bluetooth so try:
```
sudo rfkill unblock bluetooth
```
now show us:
```
sudo service bluetooth start
```

Yes, I am dual booting and it works on Windows.

Both commands return nothing

```
$ sudo service bluetooth start


```

---

### Post by #&amp;thj^% on 2019-08-24
This can be an annoying one, ;)  but lets see this then:
```
sudo dmesg | egrep -i 'r8822be'

```
And one more:
```
uname -r
```

---

### Post by ariel16 on 2019-08-25
> **1fallen said:**
> This can be an annoying one, ;)  but lets see this then:
```
sudo dmesg | egrep -i 'r8822be'

```
And one more:
```
uname -r
```

```
$ sudo dmesg | egrep -i 'r8822be'
[    3.452748] r8822be: module is from the staging directory, the quality is unknown, you have been warned.


```

```
$ uname -r
5.0.0-25-generic


```

---

### Post by #&amp;thj^% on 2019-08-26
**EDIT: Please read jeremy31's post just below mine as to not waste more time.**
**Is Secure Boot turned off?
Also post back the return for:
```
sudo modprobe -v r8822be
```
And if needed also check that **"AutoEnable=ture"** is set in **"/etc/bluetooth/main.conf".**
```
# AutoEnable defines option to enable all controllers when they are found.
# This includes adapters present on start as well as adapters that are plugged
# in later on. Defaults to 'false'.
AutoEnable=true

```

---

### Post by jeremy31 on 2019-08-26
Unless someone can find a way to get the bluetooth device to show in lsusb results, it isn't going to work

---

### Post by ariel16 on 2019-08-27
> **1fallen said:**
> **EDIT: Please read jeremy31's post just below mine as to not waste more time.**
**Is Secure Boot turned off?
Also post back the return for:
```
sudo modprobe -v r8822be
```
And if needed also check that **"AutoEnable=ture"** is set in **"/etc/bluetooth/main.conf".**
```
# AutoEnable defines option to enable all controllers when they are found.
# This includes adapters present on start as well as adapters that are plugged
# in later on. Defaults to 'false'.
AutoEnable=true

```

Obviously, Secure Boot is off so that I can boot Ubuntu.

sudo modprobe -v r8822be returned nothing. AutoEnable was set to true.

---

### Post by jeremy31 on 2019-08-27
ariel16, if you don't see a realtek device in lsusb results, there isn't a way to make the bluetooth work.  There might be some option in BIOS settings, I don't know

---

### Post by ariel16 on 2019-08-29
There is an option in the BIOS to enable/disable bluetooth and it's enabled (it works on Windows). It doesn't appear in lsusb.

```
$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 04f2:b67f Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

If it's not possible, thank you for your help. I appreciate that.

---

### Post by jcwjcw42 on 2020-01-20
FWIW, I have the same problem with Ubuntu 18.04 and later...the bluetooth side of the rtl8822be is nowhere to be found. However, I booted with an OpenSUSE Leap live iso with kernel 4.12 and a Debian Stretch install (kernel 4.9) and the bluetooth works fine there. Apparently there was a kernel regression at some point that keeps the chip from being found with the latest releases.

Is this worth reporting to the kernel developers? If so, where?

---

### Post by arijit72 on 2020-08-06
Is there any update on this? I've bumped into the same problem, tried almost everything that's there on the internet - no luck. I'm now downloading OpenSuse Leap 15.1 - but reinstalling will mean a lot of rework :-(

---

