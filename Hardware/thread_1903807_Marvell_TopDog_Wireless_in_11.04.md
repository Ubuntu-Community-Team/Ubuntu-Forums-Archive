---
title: "Marvell TopDog Wireless in 11.04"
date: 2012-01-03
forum: Hardware
---

### Post by tpkatsa on 2012-01-03
Howdy All

Working on a friend's laptop - Gateway M6752 with Marvell TopDog Wireless card.

Followed the instructions in most tutorials on how to set this up (the ndiswrapper thing etc.). 

lspci -nn looks good - marvell device is detected
sudo ndiswrapper -l   says that netmw14x driver installed and device present
iwconfig returns wireless device, managed mode, and so on

When I do iwlist scan, however, things aren't so good:

wlan 0   No scan results

Additionally, when I click the usual icon at top I don't see a list of wireless networks detected. Whereas, my own laptop, also running 11.04 (but with a different wireless card) sees all the networks with no issues.

I'm posting this because most tutorials stop with a successful ndiswrapper -l output. But they don't provide a solution when the device is present but wireless networks fail to be seen.

Additionally, when I tried to "force it" by using "Connect to a hidden wireless network" and I select WPA and put in my network key, etc., it times out without any connection.

Any assistance would be most appreciated. Thanks!

-tpkatsa

---

