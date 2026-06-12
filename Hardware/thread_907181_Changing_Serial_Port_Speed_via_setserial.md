---
title: "Changing Serial Port Speed via setserial"
date: 2008-09-01
forum: Hardware
---

### Post by bettabert on 2008-09-01
I have two computers connected together using a serial port.  On the sending computer (Ubuntu 8.04) , I open the "file" /dev/ttyS0 using java and write data to it.  On the receiving computer, I only see the data if I set the port speed to 9600.  I need the two computers to communicate using 4800 (There is a reason for this and I can't change that requirement).

I set the serial port "divisor" to 24 using setserial but the port still seems to operate at 9600 baud..Even after a fresh boot, the port is set at a divisor of 0..still only sends data at 9600.  

It is my understanding that the port speed could be set by applying the correct divisor value (i.e. 1 for 115200 and 24 for 4800)

Here is the output from setserial:

 /dev/ttyS0 -ga

/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
	Baud_base: 115200, close_delay: 50, divisor: 0
	closing_wait: 3000
	Flags: spd_normal skip_test

and after executing setserial /dev/tyyS0 divisor 24

 /dev/ttyS0 -ga
/dev/ttyS0, Line 0, UART: 16550A, Port: 0x03f8, IRQ: 4
	Baud_base: 115200, close_delay: 50, divisor: 24
	closing_wait: 3000
	Flags: spd_normal skip_test




What's more puzzling, I had this working before I installed some recommended updates from Ubuntu a few days ago.  

I can send data at any speed I want using GtkTerm. 

Any suggestions?

---

### Post by nicedude on 2008-09-01
I don't use serial ports anymore and not for a long time but I installed the app you are trying so I could read its man page and  look at this for you. I see 2 things that jump out at me.

This struck a cord since it says to use spd_cust option to allow this setting to work and I didn't see where you used it.

       divisor divisor
              This  option sets the custom divisor.  This divisor will be used
              when the spd_cust option is selected and the serial port is  set
              to  38.4kb  by the application.  This parameter may be specified
              by a non-privileged user.

And secondly I see this which points out that this program does not program the hardware.

CONSIDERATIONS OF CONFIGURING SERIAL PORTS
       It is important to note that setserial merely tells  the  Linux  kernel
       where it should expect to find the I/O port and IRQ lines of a particu&#8208;
       lar serial port.  It does *not*  configure  the  hardware,  the  actual
       serial  board,  to use a particular I/O port.  In order to do that, you
       will need to physically program the serial board,  usually  by  setting
       some jumpers or by switching some DIP switches.


Hope that helps you on your way to a solution.

---

