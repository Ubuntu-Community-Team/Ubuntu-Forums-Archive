---
title: "FS Amilo 7440 Fan is always on!"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by LeoKhan on 2005-11-15
I installed ubuntu 5.10 on my fujitsu-siemens amilo 7440 laptop. All things working fine but the cpu fan is always on. Can anyone help me?

---

### Post by maulattu on 2005-11-15
install ksensors:
sudo apt-get insall lm-sensors
sudo apt-get install ksensors
ksensors
it will show the cpu temp and the cpu usage; the fan is automaticcally turned on when temp reach about 63 or 64 &#176;C

---

### Post by LeoKhan on 2005-11-15
ksensors don't work properly because lm_sensors do not support my motherboard.

---

### Post by chantra on 2006-03-30
I've got the same think happening on my laptop (same amilo). What I do, is to run glxgears (but it in background) so it consume 100%cpu for about 5 min , once the cpu reaches 54 degrees, fan turns off :).

I can't get hibernate nor suspend to disk to work :s

---

### Post by chantra on 2006-05-09
hibernate and suspend actually do work but you need to kill X before doing so, I've submitted a bug on launchpad: [https://launchpad.net/distros/ubuntu/+bug/43708]("https://launchpad.net/distros/ubuntu/+bug/43708")

---

### Post by flixer on 2006-05-11
Hibernation works on my 7440g laptop. I just have to click hibernation in klaptop and it works just perfect. Suspend doesn't work, i'm hoping that they would come up with a fix for that.

---

### Post by chantra on 2006-05-11
same here actually.

---

### Post by barbarian on 2006-05-11
> debian/ubuntu tips and tricks

Sorry for interrupting, but, cool source, definitely being bookmarked! Thank you!

---

### Post by chantra on 2006-05-11
Thanks a lot barbarian :)

---

### Post by chantra on 2006-06-10
This seems to have been corrected in dapper. My fan is now turning off :)

---

### Post by mkor on 2006-06-11
Maybe you can try something like this [http://ubuntuforums.org/showthread.php?t=100035]("http://ubuntuforums.org/showthread.php?t=100035")

---

### Post by chantra on 2006-06-12
The good thing is that: **the problem is solved**. 
We don't need anymore tweak, the system just behave correctly now :)

---

