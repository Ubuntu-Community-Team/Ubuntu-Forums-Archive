---
title: "16550 PCI 4 Port Serial Problem"
date: 2007-06-12
forum: Hardware &amp; Laptops
---

### Post by nibther on 2007-06-12
Hi,

I have been trying for a long time to install a 4 Port PCI 16550 Serial Card, from StarTech.com, which uses NetMos chipset, without much luck.

I found their installation guide very confusing and although i am new to linux, i have shown it to very experienced users who are unsure of what to make of it.

The documentation says to look for a the pci card resource i/o port and irq by using /proc/pci, but that file doesn't exist on my dapper drake machine. At one point I was able to read in serial messages at ttyS7, except that all four serial ports were registering at ttyS7. I would attach a cable to a port and ask ttyS7 to read a line, Then I sent a string from anothe machine and it would get it. But when I pluged the cable into the other four ports the same behavior would happen for ttyS7.

Has anybody gotten this 4 port serial card to work with ubuntu. Any hints for how to properly install it.

INSTALLATION GUIDE:
This installation guide describes the procedures to install NetMos Technology Nm9735CV, Nm9745CV, Nm9835CV, Nm9845CV PCI serial ports in Linux platform.



Linux Platform



l Operating System		: RedHat, SuSe

l Terminal Emulation AP		: minicom

l Internet Dialer		: Kppp





Find the available serial ports



Since Linux only support 4 serial ports (ttyS0, ttyS1, ttyS2, ttyS3) under the default condition. Most likely, ttyS0 & ttyS1 are supported by mother board's built-in serial controllers and ttyS2 & ttyS3 are free for additional I/O card.



Serial ports could be checked by the following commands.



setserial  /dev/ttyS0 -a 		(COM-1)

setserial  /dev/ttyS1 -a 		(COM-2)

setserial  /dev/ttyS2 -a 		(COM-3)

setserial  /dev/ttyS3 -a 		(COM-4)



If COM-1 is used by mouse, the response is similar to



/dev/ttyS0 : Device or resource busy    



If the COM-1 does not attach any device, the response is similar to 



/dev/ttyS0, Line 0, 	UART: 16550A, Port: 0x3f8, irq: 4

                 	Baud_base: 115200, clos_delay: 50, divisor: 0

                 	closing_wait: 3000, closing_wait2: infinite

                 	Flags: spd_normal skip_test



In case ttyS2 (COM-3) is free, the response for command  setserial /dev/ttyS2 -a is shown below.



/dev/ttyS2, Line 2, 	UART: unknown, Port: 0x3e8, irq: 4

                     	Baud_base: 115200, clos_delay: 50, divisor: 0

                     	closing_wait: 3000, closing_wait2: infinite

                     	Flags: spd_normal skip_test



Find the PCI card resource ( I/O port address & IRQ) for the serial ports



Enter the command  more  /proc/pci



The response is similar to the following

      

			Bus 0, Device 11, function 0:

			Serial controller : Unknown vendor Unknown device (rev 01).

			Vendor id=9710, Device id=9735

					Device id=9745

					Device id=9820

					Device id=9825

					Device id=9835

					Device id=9845



			Medium devsel. Fast back-to-back capable. IRQ 11



			Board with Nm9735CV part

			I/O at 0xc000 [0xc001]	serial port 1

			       0xc008 [0xc009]	serial port 2



			Board with Nm9745CV part

			I/O at 0xc000 [0xc001]	serial port 1

			       0xc008 [0xc009]	serial port 2

			       0xc010 [0xc011]	device 1

			       0xc018 [0xc019]	device 2

			       0xc020 [0xc021]	device 3

			       0xc028 [0xc029]	device 4



			Board with Nm9820CV part

			I/O at 0xc000 [0xc001]	serial port 1

			I/O at 0xc400 [0xc401]	not used

			I/O at 0xc800 [0xc801]	not used

			I/O at 0xd000 [0xd001]	not used

			I/O at 0xd400 [0xd401]	not used

			I/O at 0xd800 [0xd801]	not used



			Board with Nm9825CV part

			I/O at 0xc000 [0xc001]	serial port 1

				

			Board with Nm9835CV part

			I/O at 0xc000 [0xc001]	serial port 1

			I/O at 0xc400 [0xc401]	serial port 2

			I/O at 0xc800 [0xc801]	not used

			I/O at 0xd000 [0xd001]	not used

			I/O at 0xd400 [0xd401]	not used

			I/O at 0xd800 [0xd801]	not used



			Board with Nm9845CV part

			I/O at 0xc000 [0xc001]	serial port 1

			I/O at 0xc400 [0xc401]	serial port 2

			I/O at 0xc800 [0xc801]	device 1

			I/O at 0xd000 [0xd001]	device 2

			I/O at 0xd400 [0xd401]	device 3

			I/O at 0xd800 [0xd801]	device 4



			Board with Nm9755CV part

			I/O at 0xc000 [0xc001]	not used

			I/O at 0xc400 [0xc401]	not used

			I/O at 0xc800 [0xc801]	device 1

			I/O at 0xd000 [0xd001]	device 2

			I/O at 0xd400 [0xd401]	device 3

			I/O at 0xd800 [0xd801]	device 4





From the  /proc/pci file, it is possible to find the PCI card's I/O port address and IRQ. Especially, the NetMos parts always shows



			Vendor id=9710, Device id=9735

					Device id=9745

					Device id=9820

					Device id=9825

					Device id=9835

					Device id=9845

	

Configure the parameters for ttyS2 or ttyS3



Enter (if ttyS2 or ttyS3 are free)



           setserial  /dev/ttyS2 port 0xc000 UART 16550A

                       irq 11 Baud_base 115200



           setserial  /dev/ttyS3 port 0xc008 UART 16550A

                       irq 11 Baud_base 115200



Check the setting for ttyS2 or ttyS3



Type setserial  /dev/ttyS2 -a



      			/dev/ttyS2, Line 2, UART: 16550A, Port: 0xc000, irq: 11

                 	Baud_base: 115200, clos_delay: 50, divisor: 0

                 	closing_wait: 3000, closing_wait2: infinite

                 	Flags: spd_normal skip_test





The ttyS2 or ttyS3 are ready for application

---

