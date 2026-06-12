---
title: "Ubuntu + Cisco Aironet 350 + WPA"
date: 2005-07-29
forum: Hardware &amp; Laptops
---

### Post by BenediktKratz on 2005-07-29
Hi all,

I am trying to get my wireless pcmcia card (cisco aironet 350) working with wpa encryption. Using the latest Ubuntu version and the most recent Ubuntu Linux kernel, the wireless card seems to work fine when using no encryption or WEP.

I do need however WPA encryption and so I spent quite some hours trying to get it working either with ndiswrapper or driverloader and wpa_supplicant. But all attempts seem to fail. As I am quite new to Linux and Ubuntu of course things may brake at a lot of steps. If you need more information just post it.

But..

If someone has some more experience in setting up such an environment maybe a short description on how to do it might do the trick ;)

Thanks,

Cheers,

Benedikt

-----
Ubuntu/Kubuntu DVD images:
[http://nginyang.uvt.nl](http://nginyang.uvt.nl)

---

### Post by luca_linux on 2005-07-29
Install wpa_supplicant or xsupplicant.

---

### Post by voljin on 2005-09-24
[QUOTE=luca_linux]Install wpa_supplicant or xsupplicant.[/QUOTE]

please stop helpless replies like this. Cisco aironet 350 doesn't work with wpa_supplicant yet. Please answer based on experience, not guessing.

---

### Post by BenediktKratz on 2005-10-19
[QUOTE=voljin]please stop helpless replies like this. Cisco aironet 350 doesn't work with wpa_supplicant yet. Please answer based on experience, not guessing.[/QUOTE]

Thanks voljin! Do you have any idea when&whether it will be supported?

---

### Post by ssalman on 2006-01-25
[quote=BenediktKratz]Thanks voljin! Do you have any idea when&whether it will be supported?[/quote]

I'm having the same issue, try [this]("http://castet.matthieu.free.fr/airo/") link. I did not try it yet .

---

### Post by selam on 2006-09-19
hi, everybody

I am very new to linux. I want to learn how to connect internet in my university. Due to WPA security, I have not been able to access to internet yet. has anybody tried the procedure given by ssalman for ubuntu+wpa+ndiswrapper? is there anybody who can tell me what to do?

---

### Post by johnficca on 2007-07-04
how do I install that new driver, my laptop is the thinkpad t40 and my card is the cisco aironet 350 mini-pci? please help I need to get on wpa 1 working badly.

---

### Post by tp21 on 2007-07-06
hi,
i am having the same problem.
i have thinkpad t40, with a wireless card: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b. although i don't know if it is model 350 or not, but i can not connect to net neither with WPA nor without.
i tried network-manager, and system:administration:network, and manually. nothing worked out, although i can see my network with the network-manager but i can not log in.
i had a look on what ssalman wrote, but i didn't found any instructions or discriptions of the airo-wpa drive!
Thinkpad T40, Ubuntu 7.04
thankx

---

### Post by bricedebrignaisplage on 2007-09-11
same issue here.
from my dmesg I gathered that WPA will only work with firmware versions 5.30.17 and higher. too bad: it's only available for windows XP (at least I haven't been able to find it anywhere). I think I will have to get a new card fully supported by Ubuntu.

It was confusing at the begining because my card seemed to work fine: the network manager was able to show the available wireless networks and corresponding signal strengths. But I was not able to obtain an IP adress from the DHCP server.

good luck

---

### Post by sztokbant on 2007-11-01
I successfully upgraded my Cisco Aironet 350 PCMCIA firmware to the latest (v5.60) version. I downloaded the WinXP firmware .EXE file, unzipped it (yes, it's a zip file) and used the redhat9 firmware update/diagnosis utility to update my card's firmware using the .IMG file.

I still didn't manage to make WPA work but now dmesg tells me the card is WPA capable...

---

### Post by rdelahoz on 2008-04-09
I had a similar problem with my wireless and Ubuntu 7.10. After trying everything the ubuntu forums recommended, I finally discovered that my wireles card did not support WPA technology. My wireless worked only with WEP. Check it out , maybe that's the problem of your wireless card.

---

### Post by Charles H. on 2008-07-10
I am using X31 PXE with a Cisco wireless card (might be 350). The funny thing is that this card works fine under Windows XP at my home WPA wireless router, but not in Ubuntu. Ubuntu is really my favorite distribution. Can anyone help?

---

