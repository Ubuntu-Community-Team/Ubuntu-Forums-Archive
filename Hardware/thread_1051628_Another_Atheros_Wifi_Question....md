---
title: "Another Atheros Wifi Question..."
date: 2009-01-26
forum: Hardware
---

### Post by jjoker0110 on 2009-01-26
Ok, Ive been all over the Internet trying to figure out why what Im doing isn't working and it is working for everyone else. I tried out the method described here: "[http://ubuntuforums.org/showthread.php?t=967654]("http://ubuntuforums.org/showthread.php?t=967654")" as well as the same or similar method on other websites. I cant seam to understand why I cant get this thing working :-/ Can anyone point me in the right direction??

---

### Post by ASchweitzer on 2009-01-27
Could you post some more information? Hardware? *lspci* output, and how/what exactly isn't working for you?

---

### Post by jjoker0110 on 2009-01-27
Haha, sorry about that, I was so in a hurry to post up that I had a problem I forgot to post my specs. I have a Toshiba Satellite P205, Intel Pentium running about 2.25 Ghz, 1Gb of DDR2 RAM, an Atheros wifi card, and let me know if I left anything out. 

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

uname -a:

```
Linux jackLap 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

```

lspci | grep -i net:

```
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```

And basically I just can't get my wireless card to do anything :-/

Did I miss anything? Thanks for the help in advance :-D

edit: What I did was, go to **Hardware Drivers** and disabled the Atheros driver, restarted, went back in and ran this command:
```
sudo aptitude install linux-backports-modules-intrepid-generic
```
and restarted again. After that, according to this and a few other forms, that should have kick started my wifi :-/

---

### Post by stchman on 2009-01-27
You have to go into System--->Administration--->Hardware Drivers and enable the Atheros 5xxx driver.  Reboot and your wireless will work!!!!

---

### Post by jjoker0110 on 2009-01-27
> **stchman said:**
> You have to go into System--->Administration--->Hardware Drivers and enable the Atheros 5xxx driver.  Reboot and your wireless will work!!!!

I know that I have to do that, sadly Atheros 5xxx is not there after running the command I specified above :-( Thats why Im confused right now.

---

### Post by jjoker0110 on 2009-01-29
Any ideas guys? Not trying to be impatient, Im just trying to do this in between classes. I appreciate any help I can get.

---

