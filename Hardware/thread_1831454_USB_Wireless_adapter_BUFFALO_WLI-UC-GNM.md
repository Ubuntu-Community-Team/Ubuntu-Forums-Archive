---
title: "USB Wireless adapter BUFFALO WLI-UC-GNM"
date: 2011-08-23
forum: Hardware
---

### Post by sumakei on 2011-08-23
Hello everyone,

I'm using the USB Wireless adapter BUFFALO WLI-UC-GNM on Ubuntu 10.04.

Using the commands below, I am able to get it working.

```

sudo -s 
aptitude build-dep linux-source 
mkdir -p ~/workspace/linux 
cd ~/workspace/linux 
apt-get source linux-image-$(uname -r)

```Add next line to /drivers/staging/rt2870/2870_main_dev.c 
```
{ USB_DEVICE(0x0411, 0x01A2) }, /* Buffalo Airstation WLI-UC-GNM */
``````
 
make -C /lib/modules/$(uname -r)/build M=$(pwd)/linux-2.6.32/drivers/staging/rt2870 modules 
make -C /lib/modules/$(uname -r)/build M=$(pwd)/linux-2.6.32/drivers/staging/rt2870 modules_install 
mv /lib/modules/$(uname -r)/kernel/drivers/staging/rt2870/rt2870sta.ko  /lib/modules/$(uname -r)/kernel/drivers/staging/rt2870/rt2870sta.ko.bak
mkdir -p /etc/Wireless/RT2870STA 
touch /etc/Wireless/RT2870STA/RT2870STA.dat 
echo Default > /etc/Wireless/RT2870STA/RT2870STA.dat 
depmod -a 
exit

```However, I wonder if there is an easier way to install this USB Wireless device?
As I have to repeat this process every time a new Kernel update comes out.

Also, how can I give this info to the guys working on Ubuntu? So they can make this device work on a fresh install, and other people who owns this device can use it too.

Thanks.

---

### Post by sumakei on 2011-09-30
hello, anybody? :)

---

### Post by mrgoodfox on 2011-10-17
I have a similar problem with Buffalo's [AirStation ]("http://www.buffalotech.com/products/wireless/client-adapters/airstation-highpower-n300-compact-usb-20-wireless-adapter-wli-uc-g300hp/")USB card.

I actually havent been able to find a solution yet though. I'm getting help on [this thread]("http://ubuntuforums.org/showthread.php?t=1863012") about it.

---

### Post by wesleybishop on 2011-10-17
Looks like this bug has also been reported [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/801248](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/801248) and has been fixed. 

"Julian Wiedmann (julianw) wrote on 2011-08-12:	 #27
Note that this is fixed in Oneiric by adding the ID to the mainline rt2x00 driver, http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-oneiric.git;a=commit;h=b3ba44c6d1633692b45910ee77064e635e2c3143"

---

