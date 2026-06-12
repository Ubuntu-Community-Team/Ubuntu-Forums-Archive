---
title: "Can't retrive and install driver for Alfa model AWUS036HN"
date: 2021-10-25
forum: Hardware
---

### Post by pad-0001 on 2021-10-25
Hi All
Setting up my home server with Ubuntu Server 20.04.3 LTS, to connect that also via wifi, i notice that i doesn't had the drivers for my Alfa device. The model is AWUS036NH and the chipset Ralink RT3070 ([https://www.alfa.com.tw/products/awus036nh?_pos=1&_sid=05558cf5c&_ss=r&variant=36481029374024](https://www.alfa.com.tw/products/awus036nh?_pos=1&_sid=05558cf5c&_ss=r&variant=36481029374024)).
I also finded the drivers archive 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.bz2 but in all way that i tried, i can't install the drivers for some error. Different ways get me different errors, if will be necessary, i can share you way/error.

I state that i never install before a driver by cmd. I tried to follow some suggestions finded online but i think that something is not well explane or I downloaded wrong drivers package.
Someone can help me?

Thanks, Pieto.

---

### Post by axelmasok on 2021-10-29
10yo adapter. Surprised it doesn't just work out of the box.
If you check dmesg and see detection you might need the firmware file and put it in the right place.

[https://files.alfa.com.tw/?dir=%5B1%5D%20WiFi%20USB%20adapter/AWUS036NEH/Linux](https://files.alfa.com.tw/?dir=%5B1%5D%20WiFi%20USB%20adapter/AWUS036NEH/Linux)

Otherwise try building the driver package from the above site on your system but I think that driver code won't compile with newer kernels if I was a bettting person...

Howto: [https://www.py4u.net/discuss/1106439](https://www.py4u.net/discuss/1106439)

---

### Post by Yellow Pasque on 2021-10-29
It should work without manual intervention. Please get more info: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

