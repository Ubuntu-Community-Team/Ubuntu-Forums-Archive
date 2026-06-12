---
title: "udev permissions in ubuntu 12.04? (avrdude and Atmel AVRISPMK2)"
date: 2012-05-24
forum: Hardware
---

### Post by pioupus on 2012-05-24
Hi,
since Ubuntu 12.04 i have a problem with my udev rules i was using in 10.04. I dont have permission to access to my USB devices like for example the Atmel AVR ISP MK2. It is a programmer for Atmel Microcontrollers. Normally with

```

avrdude -pt13 -c avrisp2 -P usb

``` i should be able to use it.  But in 12.04 this only works under sudo.


My /etc/udev/rules.d/60-avrisp.rules is:



```


SUBSYSTEM!="usb_device", ACTION!="add", GOTO="avrisp_end"  

# Atmel Corp.JTAG ICE mkII 
ATTR{idVendor}=="03eb", SYSFS{idProduct}=="2103", MODE="660", GROUP="dialout" 

# Atmel Corp. AVRISP mkII
ATTR{idVendor}=="03eb", SYSFS{idProduct}=="2104", MODE="660", GROUP="dialout" 

# Atmel Corp. Dragon
ATTR{idVendor}=="03eb", SYSFS{idProduct}=="2107", MODE="660", GROUP="dialout"

LABEL="avrisp_end"
``````
groups pioupus adm dialout cdrom sudo dip plugdev users lpadmin sambashare
```This worked without any problems in 10.04


```

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 0c45:6426 Microdia 
Bus 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 003 Device 002: ID 03eb:2104 Atmel Corp. AVR ISP mkII
Bus 003 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 004 Device 002: ID 1cb6:6651 
Bus 001 Device 008: ID 2457:101e

```Anybody knows if something has changed in udev which lets this rule to fail? Anybody has an idea what i can try for solving this problem?



Greetings,


Pioupus

---

### Post by rhenig on 2012-05-24
I found that changing SYSFS{idProduct} to ATTRS{idProduct} work for another device I was having problems with.

---

### Post by pioupus on 2012-05-25
Hi rhenig,

seems there is still another issue. I tried this without result.

Greeting,

Pioupus

---

### Post by pioupus on 2012-05-25
> **rhenig said:**
> I found that changing SYSFS{idProduct} to ATTRS{idProduct} work for another device I was having problems with.

Hi rhenig,

almost! instead of SYSFS an ATTR should be used. With  ATTR its working! thank you!

---

### Post by BrunoRegno on 2013-02-14
Thank you, Rhenig... you ended 24 hours of mystery. The official canon driver for MP-250 declares udev rules containing SYSFS... due to this the scanner cannot be shared on the network unless the usb devices are given a little chmod 666... even if the udev rule included is supposed to do it... changing SYSFS to ATTRS in the rule file made everything work like a charm. MASTER!

---

