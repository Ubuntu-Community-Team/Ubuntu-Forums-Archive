---
title: "usb-serial converter enumeration problem"
date: 2012-03-02
forum: Hardware
---

### Post by quantumbit on 2012-03-02
we have a problem with three usb-serial converters: After each reboot, the match to /dev/ttyUSBx seems to be changed and we have to reassign the tty number in our code.
Is there a way to force a device to a fixed /dev/ttyUSBx logical device?
lsusb shows the following result for our three converters

Bus 001 Device 025: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 001 Device 024: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 001 Device 022: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

Thanks for your help

---

