---
title: "Ubuntu 11.04 Network Latency"
date: 2011-07-30
forum: Hardware
---

### Post by FrustratedNoob on 2011-07-30
Hello,

I've installed Ubuntu 11.04 on a laptop and a desktop. The Laptop is an Acer 7741Z and the desktop was built by me. On both pc's both wireless and wired network cards produce an unbelievable amount of latency on the LAN. Using the wireless card on my acer provides me with 200+ ms latency when pinging my default gateway when in windows 7 I get 2-4 ms. On my custom built PC the NIC built into the motherboard is unusable, half the packets are dropped. I also have a Gigabit PCI card installed and I get 100 ms latency when pinging the gateway. Drivers are extremely hard to find, and when you do find drivers it's very difficult to install them as the commands in the read me's rarely work. Below is a list of some of the hardware that is experiencing problems:

NetLink BCM57780 Gigabit Ethernet PCIe
Broadcom BCM43225 802.11b/g/n
NIC on Asus P8H61-M motherboard 
Trendnet TEG-PCITXR 

Every wireless/wired network card I've tried so far has given me problems, where in windows they work perfectly. I like Ubuntu and everything else works fine; however if I'm going to get unacceptable performance I may have to consider other options, such as going back to windows. If anyone has some insight into what is going on and how to correct my issue, or easily upgrade drivers please please help me out.

Thanks for your time to read my lengthy post,

Dan

---

### Post by FrustratedNoob on 2011-07-30
I fixed the wireless issue I guess it has something to do with power management. The following command dropped my 200ms pings down to 2ms
[B]
sudo iwconfig eth1 power off[/B]

After hours of searching I found it on this thread:

 [http://ubuntuforums.org/showthread.php?p=10368636](http://ubuntuforums.org/showthread.php?p=10368636)

I don't know yet if I have to issue that command everytime I reboot. The wired on my laptop is good around 2 - 4 ms, so the laptop has been taken care of. My desktop however is still having issues. For now I'm using a usb NIC because it is giving me .5 ms responses from my gateway. The Gigabit PCI card is still giving me high ping times, and the NIC built into the Asus motherboard is still unusable.

---

