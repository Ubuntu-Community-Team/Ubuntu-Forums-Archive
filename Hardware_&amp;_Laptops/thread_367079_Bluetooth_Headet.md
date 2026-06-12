---
title: "Bluetooth Headet"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by mortalfunk on 2007-02-21
So I'm trying to get my Bluetooth Plantronics Headset (P590) to work in Ubuntu. I already have my bluetooth mouse working so I know that bluetooth is at least working at a basic level. Here is what I have tried and the error message I receive. I am using Kubuntu and the Acer Ferrari 4005 notebook. 

sudo apt-get install bluez-btsco
sudo modprobe snd-bt-sco
sudo hciconfig hci0 voice 0x0060
sudo hcitool scan
sudo btsco 00:03:89:93:85:11
Error: Failed to connect to SDP server: Invalid exchange
Assuming channel 2
Can't connect RFCOMM channel: Invalid exchange

If I try
sudo hidd --connect  00:03:89:93:85:11
I get
Can't get device information: Invalid exchange
along with a KBluetoothD pop-up saying "Problem connecting with 590Plantronics. Unable to pair"


Any ideas or able to pick out something i missed?

---

