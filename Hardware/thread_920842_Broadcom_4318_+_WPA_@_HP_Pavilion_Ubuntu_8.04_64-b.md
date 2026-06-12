---
title: "Broadcom 4318 + WPA @ HP Pavilion Ubuntu 8.04 64-bit"
date: 2008-09-15
forum: Hardware
---

### Post by rootslash on 2008-09-15
Hello people,

for the people that don't get the Broadcom 4318 to work on a Ubuntu 8.04 64-bit HP Pavilion:

1) Update your sources list, and do an update.

2) The weirdest step, first install b43-fwcutter and then remove it and install it again.
```

sudo apt-get install b43-fwcutter
sudo apt-get remove b43-fwcutter
sudo apt-get install b43-fwcutter

```
Of course you have to automatically let the firmware be fetched.

3) Reboot your system, after it's rebooted let's check if your Broadcom chip can find any networks. Start the terminal again:
```
sudo iwlist wlan0 scan
```
If you find some networks you're okay and it means you have your card working.

4) Get WPA-TKIP to work:
```
sudo gedit /etc/network/interfaces
```Copy and paste the following, edit the SSID and WPA KEY to your needs.```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-driver wext

wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid TYPEHEREYOURSSID
wpa-psk "TYPEHEREYOURWPAPSKKEY"


auto wlan0

```

Reboot or try the following:
```

sudo /etc/init.d/networking restart

```
If this still doesn't work try this:
```

sudo dhclient wlan0

```

I hope you got your wireless up and running by now.

RootSlash

---

### Post by DoctorMO on 2008-09-17
I wonder why you need to specify the WPA settings... doesn't this limit who can use the help? what if they're using WPA2 Enterprise?

---

