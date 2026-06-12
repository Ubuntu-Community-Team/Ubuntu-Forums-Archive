---
title: "Can't Connect Serial Port at 14400"
date: 2010-07-07
forum: Hardware
---

### Post by CNLiberal on 2010-07-07
I have a CD Duplicator.  The robotic arm talks over serial interface.  The speed it needs is 14400.  I have minicom installed.  I try to configure it with a 14400 speed, but it says it's invalid.  I cycle through the options and it jumps from 9600 to 19200.  I REALLY need 14400.  What am I doing wrong?  The board is a CRAZY old Asus A7N8X-E Deluxe.  Right now, I'm using the secondary COM port (off a breakout cable).  I'm gonna try the other port tonight.  Doubt it'll work.  Thanks!

Jim

---

### Post by recluce on 2010-07-08
> **CNLiberal said:**
> I have a CD Duplicator.  The robotic arm talks over serial interface.  The speed it needs is 14400.  I have minicom installed.  I try to configure it with a 14400 speed, but it says it's invalid.  I cycle through the options and it jumps from 9600 to 19200.  I REALLY need 14400.  What am I doing wrong?  The board is a CRAZY old Asus A7N8X-E Deluxe.  Right now, I'm using the secondary COM port (off a breakout cable).  I'm gonna try the other port tonight.  Doubt it'll work.  Thanks!

Jim

14400 is an extremely odd speed for a serial port - it might not be supported by the UART driving your COM port. Standardized speeds include 300, 600, 1200, 2400, 4800, 9600 and 19200 bps (as well as some low odd-ball speeds like 110). Most UARTs also run 38,400 and 115,200.

If your machine has a 16550 UART, almost any baud rate is possible in theory - it than becomes a driver or possibly BIOS issue.

---

### Post by CNLiberal on 2010-07-19
The machine I'm using isnt' that old.  It's an ASUS A7N8X-E Dlx.  It has the 16550A UART onboard.  But how can I get this odd speed on my Ubuntu box?  BIOS is simply set to give me specific I/O and IRQ settings.  There's nothing else in there that would help me get the correct speed.  Any pointers?  Thanks much!

Jim

---

### Post by david stevenson on 2010-07-20
There is a program called setserial which should  do what you need.
sudo apt-get install setserial
man setserial

Good luck 8-)

---

### Post by CNLiberal on 2010-07-20
I have tried setserial but its been so long that I don't remember the it outcome. It either let me and then i went to minicom and 14400 was still not an option. Or it just failed. I'll try again tonight.

---

