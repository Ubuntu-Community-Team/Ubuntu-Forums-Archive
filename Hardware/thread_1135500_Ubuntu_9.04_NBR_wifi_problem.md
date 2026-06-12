---
title: "Ubuntu 9.04 NBR wifi problem"
date: 2009-04-24
forum: Hardware
---

### Post by dj.dule on 2009-04-24
Hi all,

I just downloaded and installed fresh installation of 9.04 netbook remix on Asus EeePC 1000. I have networking problem. I connected to wifi (Huawei DSL router, WPA hidden network, DHCP) and it seems that is OK. But networking is not working. It starts working (i have throughput for few seconds) and then stops.

When I tried pinging router i have following results:

first it is pinging OK
then, packets starts to get lost
then I start having message: 
ping: sendmsg: No buffer space available

I tried both opensource and closedsource wifi drivers, same result.

Any idea what could be the problem ?

TIA

Dusan

---

### Post by GeorgeVita on 2009-04-24
Hi **dj.dule**,

Go to BIOS SETUP: keep pressing **F2** while booting

**BIOS SETUP UTILITY** > **Advanced** > **Onboard Devices Configuration**

**Enable** everything! (I was having some problems when Bluetooth was Disabled)

**F10** Save & exit.

Retry it.

Regards,
George

---

### Post by dj.dule on 2009-04-24
Unfortunately, it did not solve the problem.

I noticed following error in /var/log/messages

ath5k phy0: unsupported jumbo 

few times. I suppose this has something to do with net problem. Any idea how to solve this ?

---

### Post by dj.dule on 2009-04-24
I solved the problem using advice I found on other forum. I switched channel of my access point from 9 to 1. It seems to work at the moment.

---

### Post by macabro22 on 2009-06-02
> **dj.dule said:**
> I solved the problem using advice I found on other forum. I switched channel of my access point from 9 to 1. It seems to work at the moment.

So, should we assume you are not getting the "unsupported jumbo" messages?

---

### Post by chadk5utc on 2009-06-13
just ignore obvious parts the rest will get you going.

[http://ubuntuforums.org/showthread.php?p=7448204#post7448204](http://ubuntuforums.org/showthread.php?p=7448204#post7448204)

---

