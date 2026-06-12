---
title: "Ubuntu 16.04: installing atheros QCA9377 wireless driver makes booting problems"
date: 2016-05-14
forum: Hardware
---

### Post by guidry on 2016-05-14
[TABLE]
[TR]
              [TD="class: postcell"]        I download and install the QCA9377 driver(wifi 802.11ac) from [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)  for my  Ubuntu 16.04 64bit. Even though the wi-fi works ok, I have booting problem. It will cause boot process to fail every other time. I mean  power on, not restart. I use text mode to see the boot messages, sometimes, it Ubuntu will do something after a fail boot, So it becomes one time of success, the next time failure which means I  have to power on, power off then power on to get into the system.

  During booting process, sometimes it says
  > [INDENT]   Kernel panic - not syncing: Timeout: Not all CPUs entered broadcast   exception handler

 [/INDENT]  sometimes it hangs after RFKill
  I just follow the following link step by step. [No Wifi in Qualcom Atheros - Ubuntu 16.04 - Acer Aspire E 15]("http://askubuntu.com/questions/763080/no-wifi-in-qualcom-atheros-ubuntu-16-04-acer-aspire-e-15")
  ```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
sudo mkdir /lib/firmware/ath10k/QCA9377
sudo mkdir /lib/firmware/ath10k/QCA9377/hw1.0
cd ath10k-firmware/QCA9377/hw1.0
sudo cp *  /lib/firmware/ath10k/QCA9377/hw1.0
cd /lib/firamware/ath10k/QCA9377/hw1.0
sudo mv firmware-5.bin_WLAN.TF.1.0-00267-1  firmware-5.bin

```  If I remove the contents in /lib/firmware/ath10k/QCA9377/hw1.0 then I can boot into the system without hanging, so the firmware problem is confirmed. To prove this, I even reinstall the system, update but without installing any other programs.
  What should I do to make the driver work? There are many new notebook using this wifi interface.



  p.s. My notebook is Lenovo idealpad 300 151SK, cpu Intel® Core™ i5-6200U CPU @ 2.30GHz × 4
System Ubuntu 16.04 64bit Linux kernel 4.4.0-22
     

[/TD]
[/TR]
[/TABLE]

---

### Post by jeremy31 on 2016-05-14
I think your issues are unrelated to the wireless as I have helped quite a few with the same wireless and haven't seen any boot issues reported due to the firmware being available

Please post the result of ```
ls /lib/modules
``` and it wouldn't hurt to ```
dmesg > dmesg.txt
``` and pasting the contents of dmesg.txt at paste.ubuntu.com and post the URL

I think the 4.4.0-22 kernel has other issues as I have to use 4.4.0-21 to have my Atheros bluetooth working

Also post the result for ```
modinfo ath10k_pci; dkms status
```

Thanks

---

### Post by guidry on 2016-05-14
After removing the driver and reinstalling it again, and updating Ubuntu. The booting issue is gone.:D

---

