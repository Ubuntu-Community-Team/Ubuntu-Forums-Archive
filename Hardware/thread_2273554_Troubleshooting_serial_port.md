---
title: "Troubleshooting serial port"
date: 2015-04-14
forum: Hardware
---

### Post by pramod4 on 2015-04-14
Hello everyone,
I'am trying to connect to serial cable(DB9 connector) to the Ubuntu machine but it does not get detected. The serial port is enabled in the BIOS and I have also changed the serial port address in the BIOS with no change.
When i run the command "dmesg | grep tty"   i get
[    0.000000] console [tty0] enabled
[    0.810877] 00:02: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.831316] 00:03: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
The same result turn up even after connecting the DB9 connector to the serial port.
So can anyone help me out with this. I'am new to this kind of stuff.

Thank you

---

### Post by dino99 on 2015-04-14
Related doc:

[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)
[https://help.ubuntu.com/community/Minicom](https://help.ubuntu.com/community/Minicom)

---

