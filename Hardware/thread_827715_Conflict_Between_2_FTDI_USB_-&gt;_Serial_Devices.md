---
title: "Conflict Between 2 FTDI USB -&gt; Serial Devices"
date: 2008-06-13
forum: Hardware
---

### Post by theprax on 2008-06-13
I have been trying for hours to get my two FTDI based devices to work alongside one another, but they just wont. Here is what I currently have attached: 

Bus 004 Device 006: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 004 Device 005: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 004 Device 004: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 004 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 004 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 058f:9720 Alcor Micro Corp. USB-Serial Adapter
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000 

Attached are 3 things: 

1) a single USB to Serial port (bus 2 device 3)
2) a Lindy 4X USB to serial with an FTDI chip - which is everything on Bus 4
3)another piece of hardware using (the exact same?) FTDI chip (Bus 1 device 3) 

After testing out many different scenarios, the main issue seems to be a mix up between the two FTDI "devices 3" guys - even though they are on different buses.  The other 3 ports on the 4X have no problems, while the two FTDI boys assigned to "device 3" work initially individually, but once you try to use them at the same time, they wont work anymore. 

Anyone have any idea what I'm talking about? Do the /dev/ttyUSBx files only look for "devices" and not "buses"?

If you can't tell, I don't really have a deep understanding of what's going wrong, and how to fix it, other then to buy a USB -> Serial device with a different chip.

Thanks for your help.

---

### Post by theprax on 2008-06-13
I bypassed the problem by forcing the two FTDI chip devices to be on the same "BUS", but i was only able to do this with an extra USB hub, but the normal USB ports on my laptop, which all have their own individual buses. 

isn't this something that should be fixed?

---

