---
title: "Problem with multiple USB devices"
date: 2013-07-14
forum: Hardware
---

### Post by vmnrao on 2013-07-14
Hi All,


I'm running MINT15 / MATE on a toshiba atom laptop. I have 2 RS232-to-USB adapters I am trying to get working while both are physically connected to the computer. The problem is that I can only seem to get one of them working if the other is disconnected, and I think this is because the OS is trying to use ttyUSB0 for both of them. 


**Here's some info:**


A. Output of lsusb with all devices connected:
```
v@toshiba-linux ~ $ lsusb
Bus 001 Device 011: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 004: ID 04f2:b15d Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 04e2:1410 Exar Corp. 
Bus 004 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 1443:0007 Digilent CoolRunner-II CPLD Starter Kit
Bus 001 Device 015: ID 03fd:0008 Xilinx, Inc. 
```


B. Conflict that shows in dmesg when all devices connected:
```
v@toshiba-linux ~ $ dmesg | grep ttyUSB0
[  963.837493] vizzini 2-1:1.0: >ttyUSB0: XR21v14x usb uart device
[ 1108.068403] sysfs: cannot create duplicate filename '/class/tty/ttyUSB0'
[ 1108.069198] usb 4-1: >FTDI USB Serial Device converter now attached to ttyUSB0
```


**And here are my questions:**


1. In order to use one of the RS232-to-USB adapters, I have to run through the install instructions each time I boot, otherwise I cannot use the device. The install instructions are as follows:
```
* Make sure the Vizzini device is unplugged from the Linux host.
* Make sure that the cdc-acm driver and any previously loaded vizzini
  driver modules are not loaded.
	# rmmod cdc_acm
	# rmmod vizzini
	# modprobe -r usbserial
* Install the vizzini driver module.
	# modprobe usbserial
	# insmod ./vizzini.ko
* Plug Vizzini into the host.  You should see four devices created,
  typically /dev/ttyUSB[0-3].
```
How do I get this working so the driver is permanently installed and I do not have to go through this on every boot?


2. How can I resolve the "sysfs: cannot create duplicate filename '/class/tty/ttyUSB0" conflict and get it to enumerate the USB devices sequentially so I can use all of them without disconnecting any?


Any help / suggestions would be greatly appreciated!


Thanks,
V

---

