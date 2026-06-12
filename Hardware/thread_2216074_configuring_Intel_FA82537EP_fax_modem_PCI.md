---
title: "configuring Intel FA82537EP fax modem PCI"
date: 2014-04-09
forum: Hardware
---

### Post by ubscott on 2014-04-09
On a separate thread I've asked if there was a modem friendly enough with Ubuntu 12.04 that there is no hassle configuring it.  If I knew that I could get some kind of modem that would be easy to get going I'd pick it up.

While waiting for the result to that question, I have taken a stab at configuring the PCI internal winmodem I have.  My research turns up that some people say winmodems are impossible to get working with Ubuntu, while some other people say they have managed it.

I did a hardware survey.  I forget how I did it.  But it produced an HTML file.  This section is relevant:

id:    
communication:1
description:     Modem
product:     FA82537EP 56K V.92 Data/Fax Modem PCI
vendor:     Intel Corporation
physical id:     
1
bus info:     
pci@0000:01:01.0
version:     04
width:     32 bits
clock:     33MHz
capabilities:     pm generic bus_master cap_list
configuration:    
driver    =    serial
latency    =    64
maxlatency    =    62
mingnt    =    1
resources:    
irq    :    22
memory    :    feafe000-feafefff
ioport    :    de00(size=256)


This tells me that the irq is 22.  When doing two dmesgs, I get these results:


=========dmesg=========


[    0.646562] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.668266] serial 0000:01:00.0: PCI INT A -> GSI 21 (level, low) 

-> IRQ 21
[    0.668304] serial 0000:01:00.0: PCI INT A disabled
[    0.668331] serial 0000:01:01.0: PCI INT A -> GSI 22 (level, low) 

-> IRQ 22

[    0.668585] 0000:01:01.0: ttyS5 at I/O 0xde08 (irq = 22) is a 

16450
[    0.668712] 0000:01:01.0: ttyS6 at I/O 0xde10 (irq = 22) is a 8250
[    0.668840] 0000:01:01.0: ttyS7 at I/O 0xde18 (irq = 22) is a 

16450
[    0.668965] 0000:01:01.0: ttyS8 at I/O 0xde20 (irq = 22) is a 8250
[    0.669091] 0000:01:01.0: ttyS9 at I/O 0xde28 (irq = 22) is a 8250
[    0.669839] 0000:01:01.0: ttyS16 at I/O 0xde60 (irq = 22) is a 

8250
[    0.677032] Linux agpgart interface v0.103
[    0.677117] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    0.677151] agpgart-intel 0000:00:00.0: detected gtt size: 131072K 

total, 131072K mappable


=========dmesg | grep tty=========

mps@mps-desktop:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.509537] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.646562] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.668585] 0000:01:01.0: ttyS5 at I/O 0xde08 (irq = 22) is a 

16450
[    0.668712] 0000:01:01.0: ttyS6 at I/O 0xde10 (irq = 22) is a 8250
[    0.668840] 0000:01:01.0: ttyS7 at I/O 0xde18 (irq = 22) is a 

16450
[    0.668965] 0000:01:01.0: ttyS8 at I/O 0xde20 (irq = 22) is a 8250
[    0.669091] 0000:01:01.0: ttyS9 at I/O 0xde28 (irq = 22) is a 8250
[    0.669839] 0000:01:01.0: ttyS16 at I/O 0xde60 (irq = 22) is a 

8250

==============


...In the first listing, IRQ 22 is very near the ports ttyS6-ttyS16.  It seems to me that IRQ 22 is identified with the ports ttyS6-ttyS16.  If this is not true, is IRQ 22 not identified with any TTY port?

In CuteCom, I see /dev/tty50...tty53.  The character after tty is a Five (5), not an Ess (s).  I'm sure that dmesg is showing Ess (s), not 5.  Is this naming difference one of the reasons my modem is not being recognized?

(To confirm whether it is recognized I have used Modem Manager GUI.  It says "no devices found in system."  I also have tried Gnome PPP.  With Gnome PPP, I switch between /dev/tty50...tty53, and "detect."  I always get "No modem was found on your system." )

Is a reasonable course of action to convince Ubuntu that ttyS0 is tty50?  What steps can take me there (assuming getting a winmodem to work with Ubuntu 12.04 is possible.)  Thanks for your help.

---

