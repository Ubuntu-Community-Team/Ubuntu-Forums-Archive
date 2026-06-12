---
title: "Failed to use media build drivers on 3.14.79 kernel"
date: 2017-01-26
forum: Hardware
---

### Post by udroidc2 on 2017-01-26
Hi there,

I'm trying to get the linuxtv.org media build drivers running on my ODROID C2 with kernel 3.14.79. I want to use a PCTV520e dvb-c device. With kernel 4.x, it runs nicely. However, 4.x is not available for the C2, yet. Hence, I woule like to build adn run the media build drivers as described [here]("https://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers"). However, after installing the drivers and rebooting, I do not get a /dev/dvb/... folder. Looking at dmesg, the dvb-c device is recognized, successfully.

Where can I start looking for reasons, why the /dev/dvb/... folder is not created?

greetings
uDroidC2

---

### Post by QIII on 2017-01-26
Hello!

What distro are you running on your Odroid?

---

### Post by udroidc2 on 2017-01-27
Ubuntu Mate 16.04.1 LTS (GNU/Linux 3.14.79-102 aarch64)

---

### Post by udroidc2 on 2017-01-29
Come on! No1 ever had the problem, that a /dev/... did not occour as expected? I can't believe that. I do not need an answer about dvb devices, yet. In the first place, I need advice how to find reasons / where to look for.

---

