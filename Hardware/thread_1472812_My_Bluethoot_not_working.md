---
title: "My Bluethoot not working"
date: 2010-05-04
forum: Hardware
---

### Post by ldima55 on 2010-05-04
My Bluethoot not working what to do ?
it say that i dont have bluethoot udapter plaged in but it is in my laptop(0_0)
i got laptop a Lenovo G550 2958-K3G

T6500(2.1Ghz), 
4GB RAM, 
320GB 5400rpm HD,
 15.6in 1366x768 LCD, 
nVIDIA GeForce G 105M, 
CDRW/DVDRW, 
Intel 802.11agn wireless, 
Bluetooth, Modem, 10/100 Ethernet

plz help:confused::confused::confused:

---

### Post by ldima55 on 2010-05-05
please help me

---

### Post by ldima55 on 2010-05-07
somebody help me

---

### Post by dino99 on 2010-05-07
sudo update-pciids && update-usbids
sudo apt-get install bluez && sudo apt-get install gnome-bluetooth
hcitool scan

sudo /etc/init.d/bluetooth start

details of : lshw -l

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

