---
title: "Keyspan adapter only works after reboot on Dell M4400."
date: 2010-04-19
forum: Hardware
---

### Post by bugloaf on 2010-04-19
Our program communicates with a peripheral through a serial link using a Keyspan RS232-to-USB converter.  The program was successfully running on Ubuntu 9.10 on a Dell M70.  It could open the device file /dev/ttyUSB0 to communicate to the peripheral.  We could shut down the program, restart it, and reopen the connection multiple times without any trouble.

However, when we moved the program to a Dell M4400 laptop, also running Ubuntu 9.10, it could only connect to the peripheral once after the laptop was rebooted.  We started up the program again and tried to connect to the peripheral, the program would appear to successfully open the /dev/ttyUSB0 device, but it would act as though it wasn't receiving any data from the peripheral.  The only workaround so far is to reboot the laptop.

---

