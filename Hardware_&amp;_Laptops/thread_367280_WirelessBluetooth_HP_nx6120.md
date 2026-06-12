---
title: "Wireless/Bluetooth HP nx6120"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by puneit on 2007-02-21
Last night, I installed Ubuntu Edgy on friend's  HP nx6120 notebook computer
This machine has a micro-switch through which one can switch on and off bluetooth and wireless.
 The button by which Wifi/Bluetooth gets switched on is not working on this machine in Ubuntu but works on MS Windows XP.(dual boot)  (And the system doesn't reboot from Ubuntu. It has to  be first shutdown and then swtiched on again). 
The wifi card is dectected and is showing under networking
I have tried issuing the following command from the terminal but that doesn't work either

shivli@shivli :~$ sudo iwconfig eth0 txpower on
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth0 ; Input/output error.
shivli@shivli:~$ sudo iwconfig eth0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth0 ; Input/output error.
shivli@shivli:~$ sudo iwlist eth0 power
eth0      Current mode:on
shivli@shivli:~$ sudo iwlist eth0 txpower
eth0      unknown transmit-power information.

          Current Tx-Power:off


eth0--> is Intel Pro Wireless 2200

As far as bluetooth is concerned, I have no idea as how to even check if it  is detected in this machine.
Can someone guide me how did you get this working on this machine.

---

### Post by bctechnzl on 2007-02-26
I have an nx 6120 with wireless but without the bluetooth module installed.
for the led to be lit for wireless, you edit or create the file /etc/modprobe.d/ipw2200

and inside the file needs to be

```
options ipw2200 led=1
```

Its a great little laptop.  If you find the module for bluetooth, maybe there is a similar option.

In windows xp, the light is only ever on or off for wireless.  In ubuntu, it flashes when wireless is enabled and is solid when a connection is made, which I think is pretty cool.

HTH. Oh, I'm still using dapper on this laptop, but the 686 kernel, not the stock 386 one. My recent reading suggests I should reconfigure a kernel for the mobile centrino, I've started but not made the .deb package yet.

---

