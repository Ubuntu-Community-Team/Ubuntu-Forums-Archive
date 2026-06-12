---
title: "new pci usb card stops my NIC from working"
date: 2008-07-11
forum: Hardware
---

### Post by beaker15 on 2008-07-11
hi
here's what happened:

Ubuntu server was working fine, eth0 - my NIC (pci card) was working perfectly. 

I added a USB port pci card and rebooted, now it won't connect to the network. I check ifconfig and get a MAC address and other bits for eth**1** (not sure what this is, maybe an onboard controller?). No IP address though. I input the static IP details i use to eth1 and it still doesn't work.

I shutdown and take the USB card out and reboot and the network settings are back to normal. It works again.

I reboot again with the card in to try and figure out the problem (which obviously arises again) but no luck.

I take the card out again and boot it up but this time the network error is back even without the USB card in this time.

Could this be an IRQ issue? or is it something simple i'm missing

thanks for any replies, its really bugging me

---

### Post by beaker15 on 2008-07-11
for anyone interested, i've solved this. I needed a quick fix so just replaced the NIC and now i have a perfectly working eth2 interface

---

