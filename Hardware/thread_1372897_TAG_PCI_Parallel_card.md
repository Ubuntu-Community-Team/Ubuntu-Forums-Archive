---
title: "TAG PCI Parallel card"
date: 2010-01-05
forum: Hardware
---

### Post by anshuman2009 on 2010-01-05
Hi,
 
I have added a TAG PCI parallel port card on a PC which uses Ubuntu 8.04 Hardy Heron. I get the following response for "lspci -v" command:
 
"
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
I/O behind bridge: 0000e000-0000efff
Memory behind bridge: feb00000-febfffff
Capabilities: [50] 
Subsystem: Elitegroup Computer Systems Unknown device 2633
"
 
 
It does not mention a Parallel controller, only a PCI bridge. Also no I/O ports are mentioned.
 
 
Following are the install instructions for Linux that came with the PCI Parallel card:
"
*3-install and uninstall CH352 PCI to one parport*
*(1)install *
*<1>-copy install_p_80x86.o to /usr/sbin *
- Done this
 
*<2>-Add /usr/sbin/install_p_80x86 at the end of the /etc/rc.d/rc.local.*
 
- I could not find /etc/rc.d directory. But there was a /etc/rc.local file which I have edited as follows:
 
"
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/sbin/install_p_80x86
exit 0"
 
*<3>-reboot*
*The LP1 and LP2(if you inster two boards) are ready for application.*
"
 
Even after doing this, I still can't see the parallel controller in 'lspci -v' command.
 
 
What could be the possible reasons for Ubuntu to not detect PCI parallel card properly? Could it be that this particular PCI card is incompatible with Ubuntu?
 
 
Regards,
 
Anshuman

---

### Post by jamenlang on 2011-03-07
did you ever get this  figured out? ubuntu 2.6.35-22-generic lists the following for the controller

04:03.0 Serial controller: Device 4348:5053 (rev 10) (prog-if 02 [16550])
    Subsystem: Device 4348:5053
    Flags: medium devsel, IRQ 20
    I/O ports at ec00 [size=8]
    I/O ports at e880 [size=8]
    Kernel driver in use: serial

I wonder how i can force the Kernel driver to parallel.

---

