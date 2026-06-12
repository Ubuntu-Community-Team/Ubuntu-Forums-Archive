---
title: "Bluetooth Asus N53S"
date: 2011-09-15
forum: Hardware
---

### Post by alenergy on 2011-09-15
I have solved the non working Bluetooth adapter:
MC Networks 
Id under Ubuntu 11.04 = 1313:3304

I just have followed this instructions :p:p obtained from other post

I've got the same laptop (ASUS K53SV) with the same combo-card. 
I got it working with the dkms-driver on Ubuntu 11.04 64bits (kernel 2.6.38-10-generic):
1. download the driver:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/+attachment/1913129/+files/ar3011-dkms_1.1ryu2.3_all.deb](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862/+attachment/1913129/+files/ar3011-dkms_1.1ryu2.3_all.deb)
2. install the driver:
sudo dpkg -i ar3011-dkms_1.1ryu2.3_all.deb dell-laptop-dkms_1.4_all.deb
3. Check the installation:
run "dkms status" to see if there are the following info:
ar3011-dkms, 1.1ryu2.3, 2.6.38-10-generic, x86_64: installed (or similar)

After a reboot, the bluetooth icon should appear and indicate that bluetooth is working.

---

