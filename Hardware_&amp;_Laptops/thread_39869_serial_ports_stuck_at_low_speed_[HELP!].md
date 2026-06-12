---
title: "serial ports stuck at low speed [HELP!]"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by voidlogic on 2005-06-06
](*,)  I noticed this bug when I tried using an external modem. The I have verified the modem, and while though under both Ubuntu Linux 5.04 and Windows XP SP2 it will connect to the ISP at ~48k. The serial port which operates at 115.2 Kbps under windows, yet operates at a much lower speed speed under Ubuntu. I saw it suggested on these forums ina modem thread to manualy set the serial port speed, so I attemped this (was it the ppp/provider file, I can't recall, I'm booted off Windows on an external SCSI drive at the moment  :-# ). However, the line I had to this file that is supposed to set the speed it reset every time I check after the ISP is dialed. This  did not happen with FC2. Any ideas? My external modem is a SupraExpress 56k. Please help.

voidlogic

---

### Post by voidlogic on 2005-06-07
PLEASE SOMEONE- I loathe using windows!  ](*,)   ](*,)   ](*,)

---

### Post by Zerksis on 2005-06-12
I had a similar problem with a serial modem.

I used the fix described in Bug 8890 at bugzilla.

Open the file /etc/ppp/peers/ppp0 with

$ sudo gedit /etc/ppp/peers/ppp0

and add the following line at the end

115200

just the number - nothing else.

This will set the speed of the serial interface.

Hope this works for you too

Z

---

### Post by voidlogic on 2005-06-13
I will try again, but this line keeps getting removed after i dial. I don't get it. Any ideas? Is there a way to make it so NOTHING as write permissions to it?

---

### Post by Zerksis on 2005-06-13
Had a look at my ppp0 file - file owner is root.

So, try  [FONT=Courier New]**gedit /etc/ppp/peers/ppp0**[/FONT]
from a root terminal,

Applications -> System Tools -> Root Terminal

It might complain - but gedit will save the change.

*chmod* is the cmd to change file permissions - but use with care as it can lead to problems.  If you want to try setting the file read only (when you are sure that the new line has been saved) then;-

**chmod 444 /etc/ppp/peers/ppp0**

will assign read-only permission to the file for everyone.

Z

---

### Post by desdinova on 2005-06-13
try puttint it instead in /etc/ppp/options

---

