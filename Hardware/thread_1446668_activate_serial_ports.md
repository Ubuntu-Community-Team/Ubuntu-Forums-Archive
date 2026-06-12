---
title: "activate serial ports"
date: 2010-04-04
forum: Hardware
---

### Post by jbfriend on 2010-04-04
i purchased and installed a PCI one serial port and 2 USB port card. Ubuntu 9.10 sees all the new ports, activated the USB ports immediately and they are now in use by an Iomega 80GB USB drive. i have found no way to open the serial ports. 

when i installed U 9.10 it recognized everything connected to the motherboard and activated every port, printer, monitors, etc. there is one serial port on the motherboard and that is functional.

i can find no way to make USB to serial adapter work either.


jack@jack-desktop:~$ setserial -g /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3


any help to activate ttyS3 would be appreciated. that is the new serial port that actually exists when i boot to Windows. according to WinXP 4 is the number but i have no idea why Ubuntu has a ttyS1 and ttyS2.

thanks

jack

---

