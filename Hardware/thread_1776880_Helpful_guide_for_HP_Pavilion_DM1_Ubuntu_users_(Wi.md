---
title: "Helpful guide for HP Pavilion DM1 Ubuntu users (Wifi, Video, Sound Solution)"
date: 2011-06-06
forum: Hardware
---

### Post by buknoii on 2011-06-06
Hi there! I've recently purchased an HP Pavilion DM1 and for sure you experienced the following problems

* Wifi not working
* Video Card not working
* Headphones not working

Anyways regarding with the headphones it works perfectly in Ubuntu 10.04 and not in Ubuntu 10.10, and please if you are using Ubuntu 10.04 and your laptop hibernates you'll be surprised that your headphones won't work. Restarting wont do the fix, you need to restart your alsa-mixer and totally shutdown your laptop.


For the WiFi below are the instruction (**thanks to 6by9.net**)


Go to _[https://build.opensuse.org/package/binaries?package=rt5390sta&project=driver%3Awireless&repository=11.4-update](https://build.opensuse.org/package/binaries?package=rt5390sta&project=driver%3Awireless&repository=11.4-update)_

You'll see 64-bit (x86_64) and 32-bit (i586) packages listed. Download the openSUSE driver package - the source RPM, not the binary package: **rt5390sta-2.4.0.4-7.1.src.rpm**

Open your web browser's download directory and double-click the src RPM. Extract all files into a new directory named openSUSE_rt5390sta_driver

Open a terminal and sudo to root:
sudo su -
cd openSUSE_rt5390sta_driver
tar jxvf 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.tar.bz2
cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/
patch -p0 < ../rt5390sta-2.4.0.4-config.patch
patch -p0 < ../rt5390sta-2.4.0.4-WPA-mixed.patch
patch -p0 < ../rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch
patch -p0 < ../rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch
patch -p0 < ../rt5390sta-2.4.0.4-return_nonvoid_function.patch
patch -p0 < ../rt5390sta-2.4.0.4-reduce_debug_output.patch
mv RT2860STA.dat RT5390STA.dat
vi os/linux/config.mk

Change HAS_ANTENNA_DIVERSITY_SUPPORT to:
HAS_ANTENNA_DIVERSITY_SUPPORT=y

make
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA/
cp -i os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
echo rt5390sta >> /etc/modules
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
depmod -a




For the Video Card just follow the steps at **_[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)_**

---

