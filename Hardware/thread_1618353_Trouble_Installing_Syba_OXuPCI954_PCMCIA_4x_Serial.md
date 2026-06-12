---
title: "Trouble Installing Syba OXuPCI954 PCMCIA 4x Serial Port Expansion"
date: 2010-11-10
forum: Hardware
---

### Post by wmccafferty on 2010-11-10
Hello,

I've been working on getting a dumb, 4-port serial expansion PCMCIA installed and working on Lucid for a few days now.  (Info about this product is [here]("http://www.amazon.com/Syba-Connectivity-PCMCIA-Serial-Fan-Out/dp/B002TLT97I/ref=sr_1_1?ie=UTF8&qid=1289416242&sr=8-1") and [here]("http://www.plxtech.com/products/uart/oxupci954").)  Despite the steps I have taken, detailed below, I cannot communicate with any serial devices via the expansion port as I can using a USB-to-serial converter via a USB port.

Here are the steps I have taken thus far:

[LIST]
[*]Enabled ports ttyS4-S7 by taking the following steps:

[LIST]
[*]Edited /etc/default/grub and modified the GRUB_CMDLINE_LINUX_DEFAULT setting to reflect the following:  
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash 8250.nr_uarts=8"
[*]Ran "sudo update-grub"
[*]Reboot
[*]Ran "cat /proc/tty/driver/serial" to verify that the ttyS4-S7 were then available (they were).
[/LIST]

[*]Ran "lspci -v" to get the details of the card, as shown below:

16:00.0 Serial controller: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 0 (Uart) (rev 01) (prog-if 06)
Subsystem: Oxford Semiconductor Ltd Device 0000
Flags: medium devsel, IRQ 16
I/O ports at 8020 [size=32]
Memory at 80000000 (32-bit, non-prefetchable) [size=4K]
I/O ports at 8040 [size=32]
Memory at 80001000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [40] Power Management version 2
Kernel driver in use: serial

16:00.1 Bridge: Oxford Semiconductor Ltd OX16PCI954 (Quad 16950 UART) function 1 (8bit bus) (rev 01)
Subsystem: Oxford Semiconductor Ltd Device 0000
Flags: medium devsel, IRQ 16
I/O ports at 8060 [size=32]
Memory at 80002000 (32-bit, non-prefetchable) [size=4K]
I/O ports at 8080 [size=32]
Memory at 80003000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [40] Power Management version 2
Kernel driver in use: serial

[*] Ran the following to assign the appropriate ports (I've tried doing this for just the first one to see if I could get just one working...I couldn't).  Each command seems to execute successfully:

sudo setserial /dev/ttyS4 port 0x8020 irq 16 uart 16950 baud_base 1152000
sudo setserial /dev/ttyS5 port 0x8040 irq 16 uart 16950 baud_base 1152000
sudo setserial /dev/ttyS6 port 0x8060 irq 16 uart 16950 baud_base 1152000
sudo setserial /dev/ttyS7 port 0x8080 irq 16 uart 16950 baud_base 1152000
[/LIST]

At this point, I would expect to be able to connect to a serial port and initiate communications.  If I run "tail -f /var/log/messages" before connecting to one of the serial ports in the expansion card, no additional information gets shown in the "tail" window; but, if I connect my serial device using a USB-to-serial adapter, connection information gets shown in the "tail" window and I'm able to communicate with the device.  I would rather communicate via the expansion port than to have to get a number of USB-to-serial adapters and use up all of my USB ports (which I need for other purposes).

Am I missing a step...I've read and dissected just about every scratch of text which talks about setting up serial ports for Ubuntu...I'm at a loss as to what to try next.

Thank you very much for any assistance you might be able to provide!

Billy McCafferty
[http://www.sharprobotica.com]("http://www.sharprobotica.com")

---

