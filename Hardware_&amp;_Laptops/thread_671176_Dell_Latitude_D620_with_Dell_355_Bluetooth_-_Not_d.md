---
title: "Dell Latitude D620 with Dell 355 Bluetooth - Not detected"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by Deval on 2008-01-18
I've checked a whole bunch of threads already on this topic, and for the life of me, I can not get my bluetooth card to work on my Ubuntu 7.10 install.

Laptop specs:
Dell Latitude D620
Intel Core 2 Duo 1.8ghz
2GB of RAM
60GB SATA drive
Intel 3495 Wifi card
Dell 350 Bluetooth card

I checked the bios, and the card is enabled, but the kernel does not even detect the card. 

I'm a Linux newbie, just trying it out for the 1st time, so any suggestions or ideas would be great. 

I opened the terminal window, and typed in "hcitool dev" and it came back with:

Devices: 

so I typed in: "sudo hciconfig hci0 reset" which came back with:

Can't get device info: No such device

ideas? help?

-- I actually have a Dell 350 Bluetooth, not 355...sorry

---

