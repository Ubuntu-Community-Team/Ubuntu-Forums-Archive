---
title: "Only 4 serial ports for Ubuntu &gt;= 6.10. Help"
date: 2007-11-26
forum: Hardware &amp; Laptops
---

### Post by craftybones on 2007-11-26
Hello,

My company uses several pieces of hardware hooked to a computer via serial ports, often > 4 hardware devices. 

Up until Ubuntu 6.06, all these ports would get detected by default(several of these ports are add on PCI cards), but for 6.10 and above, only 4 serial ports get detected.

Is there a kernel limit on 2.6.17 and above? Do I need to recompile the kernel in order to see the other ports? Can it be done without? I've looked a lot for this on google and had not too many relevant hits.

Can somebody please help us with this? I have dmesg output posted at the end of this message.

Thank you,

craftybones

Following is 6.06 output:

iris@iris-desktop:~$ dmesg | grep ttyS
[17179572.076000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.076000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.076000] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[17179572.076000] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[17179572.080000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.080000] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.080000] 00:0a: ttyS2 at I/O 0x3e8 (irq = 11) is a 16550A
[17179572.080000] 00:0b: ttyS3 at I/O 0x2e8 (irq = 10) is a 16550A
[17179572.080000] 00:0c: ttyS4 at I/O 0x2d8 (irq = 11) is a 16550A
[17179572.080000] 00:0d: ttyS5 at I/O 0x2e0 (irq = 10) is a 16550A
[17179572.084000] 0000:00:08.0: ttyS6 at I/O 0xec00 (irq = 5) is a
16550A
[17179572.084000] 0000:00:08.0: ttyS7 at I/O 0xe880 (irq = 5) is a
16550A
[17179572.084000] 0000:00:08.0: ttyS8 at I/O 0xe800 (irq = 5) is a
16550A
[17179572.084000] 0000:00:08.0: ttyS9 at I/O 0xe480 (irq = 5) is a
16550A 

-----------------------------------------------------------------------------------------------

Following is 6.10/7.04 output:

 
iris@MAICAB02:~$ dmesg | grep ttyS
[   31.728750] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.729218] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.729623] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[   31.730014] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[   31.730863] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.731477] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.732079] 00:0b: ttyS2 at I/O 0x3e8 (irq = 11) is a 16550A
[   31.732765] 00:0c: ttyS3 at I/O 0x2e8 (irq = 10) is a 16550A


-------------------------------------------------------------------------------------------------

---

### Post by craftybones on 2007-11-26
A followup:

Apparently doing this seems to give me an idea as to what the problem is. I wonder if this actually is a boot time option and if getting rid of the line CONFIG_SERIAL_8250_RUNTIME_UARTS gets rid of it(6.06 doesn't have that line).

saikr@maicab01:/boot$ grep SERIAL config-2.6.20-15-generic | grep UAR
CONFIG_SERIAL_8250_NR_UARTS=48
CONFIG_SERIAL_8250_RUNTIME_UARTS=4


Will try and let you know,

Thank you,

craftybones

---

