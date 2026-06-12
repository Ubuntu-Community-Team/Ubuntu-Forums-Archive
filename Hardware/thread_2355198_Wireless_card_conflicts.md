---
title: "Wireless card conflicts"
date: 2017-03-10
forum: Hardware
---

### Post by anatoly.venzekov on 2017-03-10
Hi everybody,
 
I have been working for a couple of months with two wireless cards: Addon Nwu272Ev2 (chipset rtl8192cu) and Alfa AWUS051NH (chipset Railink RT3572) for pentesting purposes. The issue is that I can use whatever of them with aircrack-ng for sniffing or packet injection (airodump-ng) inside Kali Linux 2016.2, but on the other hand inside Ubuntu 16.04 I can only do this with the Adon dongle. Its is a bit weird because it seems that Ubuntu is not allowing the functionalities of aircrack-ng. At last, i have to highligth that in both OS I can see that both dongles are perfectly connected. Therefore, I have two questions:
1) Why this two dongles are working fine in Kali Linux and not in Ubuntu 16.04, although both of them are perfectly connected?
2) Is there any setting (kernel, drivers …) that I could apply to Ubuntu 16.04 to get my Alfa dongle fully operative with aircrak-ng?
 
Thanks in advance!

---

### Post by cariboo on 2017-03-10
We don't support aircrack here, but what driver does the card in question use on kali?

It looks like you may have to install the driver by hand, see [this]("http://askubuntu.com/questions/419984/install-rt3572-driver-for-asus-usb-n53-adapter")

---

