---
title: "Laptop- Bluetooth"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by wasert on 2007-08-09
Hi

I installed linux on my laptop. I've got everything working fine now, well except for the s-video out, and bluetooh... I don't have a need for the video out, but It would be reall nice to use bluetooth to connect to my phone

I installed bluez-utils and followed the instructions on: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

but, no usb devices are detected. here's the output of lsusb and hcitool dev

```

~$ lsusb
Bus 005 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```

```

~$ hcitool dev
Devices:


```

---

### Post by nconceicao on 2007-08-12
I currently am having the same problem with my Toshiba and luck? getting the bluetooth going?

---

### Post by designwiz on 2007-08-12
Make sure u bluetooth/wifi is on i.e the radio button is switched to on. On the Dell Xps m1210 its place on the rite side, its normally the button used to activate bluetooth/wifi

Once that is done u should be abe to see the bluetooth light on ur laptop

then

> sudo hciconfig hci0 inqmode 0

after that type 
> hcitool scan

works fine for me!
Regards

---

### Post by fcastillo on 2007-08-25
that doesn't work for me, because my Bluetooth device is not being recognized. I've done:
> hcitool dev
and i get
> Devices:
Nothing is displayed, but when i connect a usb Bluetooth device, my laptop recognize it and i can use it. But the internal one is not beign recognized. Any help out there????

---

### Post by pyre on 2007-08-26
Seems like it might be the same problems as they are having in [this thread]("http://ubuntuforums.org/showthread.php?t=497092").  What are the results of lsusb and dmesg?  What version of Ubuntu?  (someone in the thread said their bluetooth stopped working on Fiesty)

---

