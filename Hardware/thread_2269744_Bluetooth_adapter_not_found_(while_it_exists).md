---
title: "Bluetooth adapter not found (while it exists)"
date: 2015-03-17
forum: Hardware
---

### Post by ofnuts on 2015-03-17
Unable to use my Bluetooth. System settings says "No adapters found". lsusb reports:

```

Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]

```

It worked before so this sad state of affairs could be the results of a bad move on my part.

Running Kubuntu 14.04 on a Lenovo ThinkPad T430.

Any ideas?

PS: not the side switch, because it also disables the WiFi....

---

### Post by jeremy31 on 2015-03-21
A kernel update has required some Broadcom bluetooth devices to need firmware
```
wget https://www.dropbox.com/s/p6h7ho21fct2pzb/fw-0a5c_21e6.hcd
```
```
sudo cp fw-0a5c_21e6.hcd /lib/firmware/
```
```
sudo cp fw-0a5c_21e6.hcd /lib/firmware/brcm/
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```
Then see if there are any firmware errors
```
dmesg | tail
```

---

### Post by ofnuts on 2015-03-29
Well, last night I had the BlueTooth enabled on my phone and when I got near my PC they started to talk to each other, so it looks things fixed themselves.

---

### Post by coldraven on 2015-03-29
> **jeremy31 said:**
> A kernel update has required some Broadcom bluetooth devices to need firmware
```
wget https://www.dropbox.com/s/p6h7ho21fct2pzb/fw-0a5c_21e6.hcd
```
```
sudo cp fw-0a5c_21e6.hcd /lib/firmware/
```
```
sudo cp fw-0a5c_21e6.hcd /lib/firmware/brcm/
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```
Then see if there are any firmware errors
```
dmesg | tail
```

The bluetooth on my Compaq 6715b stopped working after upgrading to 14.04.
I followed your steps, dmesg tail said something like "New interface found" but after a reboot no bluetooth adaptor is found. :(

---

### Post by jeremy31 on 2015-03-29
Are there any BIOS updates for the Compaq and have you tried the 3.16.0-x Ubuntu kernels?  From your old post your device should show in lsusb as ID 03f0:171d and doesn't need any firmware that I know of

Some searching shows that kernel 3.11 might work from Ubuntu 13.10 so it could be a regression

---

