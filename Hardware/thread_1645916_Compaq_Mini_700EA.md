---
title: "Compaq Mini 700EA"
date: 2010-12-15
forum: Hardware
---

### Post by Lanester on 2010-12-15
Hi,

I have just installed Ubuntu 10.10 for my Compaq Mini 700EA netbook and cannot get the wireless to work. It is saying the firmware is missing when looking at the wireless icon.

I am completely new to linux/unbuntu so please be patient.

Therefore how do i resolve this? I believe the wireless chipset is from broadcom.

Thanks in advance.

---

### Post by cipherboy_loc on 2010-12-15
Open up a terminal (Applications -> Accessories -> Terminal) and type in:
```

lspci | grep -i 'net'

```

That will tell us what type of wireless card you have. Then we can decide if you need a driver for it.

*EDIT: Make sure you can run an Ethernet cable to the device. We might need to install software for it to work. Due to the fact that some major corporations "secure" their code (put it under a restrictive license), Ubuntu cannot share that code, nor the binary (what the code gets compiled into). Thus, you have to download the driver yourself for you to get what they (Ubuntu) could not rightfully distribute. 


Cipherboy

---

### Post by Lanester on 2010-12-15
The text I am getting back is;
```
01:00.0 Network Controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

---

### Post by cipherboy_loc on 2010-12-16
Then in a terminal type:

```
sudo apt-get install firmware-b43-installer
```


This will prompt you for a password, then it might ask if you want to install this and a few other packages. Press y, and then the enter key. It will then download and install the files (make sure you are plugged into the ethernet cable). Reboot, and you should be good to go.



Cipherboy

---

### Post by cipherboy_loc on 2010-12-16
There is this page that you might want to look at:

[http://linuxwireless.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian](http://linuxwireless.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian)


It gives a link to a Ubuntu page on the b43 series of Wireless drivers (

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

)

---

