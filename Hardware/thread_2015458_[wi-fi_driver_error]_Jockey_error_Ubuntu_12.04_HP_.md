---
title: "[wi-fi driver error] Jockey error Ubuntu 12.04 HP probook 4420s"
date: 2012-07-03
forum: Hardware
---

### Post by aabhasABL on 2012-07-03
Hello Everyone!
I installed ubuntu just a few days ago as i iwanted to compile cyanogen mod and other stuff for my phone.
But after installing ubuntu, installing all the updates, when i rebooted, the wifi didnt worked.
A quick Google search confirmed it was a common error. the error related to jokey.

When i do system settings > additional drivers, it shows broadcom driver not activated, and when i try to activate it, i get the common error, 


```
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```I have tried all the fixes available on the net, but nothing worked! :confused:

Any help will be greatly appreciated! :)

Here are the details of the wifi board...

43:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)

Please help as i want my phone to have CM7 atleast! :lolflag:

---

### Post by chili555 on 2012-07-03
Can you please hook up the ethernet temporarily and do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```Detach the ethernet when it's done and do:```
sudo modprobe wl
```You should be all set.

---

### Post by aabhasABL on 2012-07-05
> **chili555 said:**
> Can you please hook up the ethernet temporarily and do:```
sudo apt-get install --reinstall bcmwl-kernel-source
```Detach the ethernet when it's done and do:```
sudo modprobe wl
```You should be all set.

Unfortunately, dosent works....  :(

Here is the error i get.

```
sudo modprobe wl
[sudo] password for aabhas: 
FATAL: Module wl not found.
FATAL: Error running install command for wl

```so now what i can try, other than a complete reinstall of ubuntu?

Edit...  One more thing, if i scan wifi via terminal,  Then it shows the wi fi networks available! o.O
```
sudo iwlist wlan0 scan
```

---

### Post by chili555 on 2012-07-05
What was the result of this? Error? Warning? Or anything significant?> sudo apt-get install --reinstall bcmwl-kernel-source

---

### Post by aabhasABL on 2012-07-05
> **chili555 said:**
> What was the result of this? Error? Warning? Or anything significant?

Did what it said...  Reinstalled driver successfully.



Sent via HTC Explorer running abl e rom.

---

### Post by chili555 on 2012-07-05
> Reinstalled driver successfully.Meaning what? That your wireless works perfectly now??

---

### Post by aabhasABL on 2012-07-05
> **chili555 said:**
> Meaning what? That your wireless works perfectly now??

Erm    I guess driver is installed and it even scans and shows the wifi networks available but via terminal only. I cannot connect to a wireless network. I will rerun the commands and post the output here... I'm really a beginner in open source for PC  :)

---

### Post by chili555 on 2012-07-05
Please run and post:```
lsmod | grep -e wl -e b43
iwconfig
```Thanks.

---

### Post by aabhasABL on 2012-07-07
> **chili555 said:**
> Please run and post:```
lsmod | grep -e wl -e b43
iwconfig
```Thanks.

Here is the output.

```
lsmod | grep -e wl -e b43
rndis_wlan             37554  0 
cfg80211              205544  1 rndis_wlan
rndis_host             13848  1 rndis_wlan
usbnet                 26212  3 rndis_wlan,rndis_host,cdc_ether
aabhas@aabhas-HP-ProBook-4420s:~$ iwconfig
lo        no wireless extensions.

usb0      no wireless extensions.

eth0      no wireless extensions.

```

Edit   Now it dosent even scans the wifi networks via terminal. :-(

---

### Post by chili555 on 2012-07-07
Please do:```
sudo modprobe wl
```Any errors or warnings? No? Good! Now, please do:```
sudo su
echo wl >> /etc/modules
exit
```> rndis_host             13848  1 rndis_wlan
usbnet                 26212  3 rndis_wlan,rndis_host,cdc_etherDo you have a USB wireless device installed now? Please remove it and let us have your results.```
sudo iwlist eth1 scan
```

---

### Post by aabhasABL on 2012-07-13
> **chili555 said:**
> Please do:```
sudo modprobe wl
```Any errors or warnings? No? Good! Now, please do:```
sudo su
echo wl >> /etc/modules
exit
```Do you have a USB wireless device installed now? Please remove it and let us have your results.```
sudo iwlist eth1 scan
```

:mad:  Dosent works...  i get 2 errors on the first command itself.

```
FATAL: Module wl not found.
FATAL: Error running install command for wl

```

with or without my usb tethering enabled or disabled...  i get the same result. :(

---

### Post by chili555 on 2012-07-13
Hmmm. I thought the reinstall of the STA driver went well. Let's check:```
sudo dpkg -s bcmwl-kernel-source
```

---

### Post by aabhasABL on 2012-07-16
> **chili555 said:**
> Hmmm. I thought the reinstall of the STA driver went well. Let's check:```
sudo dpkg -s bcmwl-kernel-source
```

Getting more weirder!  it says installed correctly...

```

Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 3432
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: bcmwl
Version: 5.100.82.38+bdcom-0ubuntu6.1
Replaces: bcmwl-modaliases
Depends: dkms, linux-libc-dev, libc6-dev, linux-headers-generic | linux-headers
Conflicts: bcmwl-modaliases
Description: Broadcom 802.11 Linux STA wireless driver source
 This package contains Broadcom 802.11 Linux STA wireless driver
 for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,
 BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based
 hardware.
Modaliases: wl(pci:v000014E4d00000576sv*sd*bc*sc*i*, pci:v000014E4d00004311sv*sd*bc*sc*i*, pci:v000014E4d00004312sv*sd*bc*sc*i*, pci:v000014E4d00004313sv*sd*bc*sc*i*, pci:v000014E4d00004315sv*sd*bc*sc*i*, pci:v000014E4d00004328sv*sd*bc*sc*i*, pci:v000014E4d00004329sv*sd*bc*sc*i*, pci:v000014E4d0000432Asv*sd*bc*sc*i*, pci:v000014E4d0000432Bsv*sd*bc*sc*i*, pci:v000014E4d0000432Csv*sd*bc*sc*i*, pci:v000014E4d0000432Dsv*sd*bc*sc*i*, pci:v000014E4d00004353sv*sd*bc*sc*i*, pci:v000014E4d00004357sv*sd*bc*sc*i*, pci:v000014E4d00004358sv*sd*bc*sc*i*, pci:v000014E4d00004359sv*sd*bc*sc*i*, pci:v000014E4d0000435Asv*sd*bc*sc*i*, pci:v000014E4d00004727sv*sd*bc*sc*i*, pci:v000014E4d0000A99Dsv*sd*bc*sc*i*)
Original-Maintainer: Alberto Milone <alberto.milone@canonical.com>
```

---

### Post by chili555 on 2012-07-16
Please do:```
sudo depmod -a
sudo modprobe wl
```*Now* does it error out? Also, please run and post:```
lsmod | grep -e b43 -e bcma
```Thanks.

---

### Post by aabhasABL on 2012-07-19
> **chili555 said:**
> Please do:```
sudo depmod -a
sudo modprobe wl
```*Now* does it error out? Also, please run and post:```
lsmod | grep -e b43 -e bcma
```Thanks.

No..  i get the error ...

```
WARNING: Can't read module /lib/modules/3.2.0-23-generic/module.ko: No such file or directory
```

and rest is something like...

```
 sudo modprobe wl
FATAL: Module wl not found.
FATAL: Error running install command for wl
aabhas@aabhas-HP-ProBook-4420s:~$ lsmod | grep -e b43 -e bcma
aabhas@aabhas-HP-ProBook-4420s:~$ lsmod | grep -e b43 -e bcma
aabhas@aabhas-HP-ProBook-4420s:~$ 


```

it simply goes on repeating from lsmod | grep -e b43 -e bcma

:(

---

### Post by aabhasABL on 2012-07-29
No help with this?? 
seems like i will need to use my phone as the wireless card! :(:mad:

---

### Post by chili555 on 2012-07-29
Please try:```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo apt-get install --reinstall linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
```Those tick-marks are on the left side of my US keyboard on the same key with ~.

Now do:```
sudo modprobe wl
```Any improvement?

---

### Post by wulgulmerang on 2012-08-06
That solved the sudo modprobe wl issue.

Wifi is working again! :-)  

EasyTether from the Android Market (it's free) gave me a tethered USB internet connection, in order access this solution.

Macbook 13.3 / late 2007 / BROADCOM 4321

---

