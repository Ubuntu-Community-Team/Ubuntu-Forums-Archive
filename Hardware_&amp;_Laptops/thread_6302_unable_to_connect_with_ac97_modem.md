---
title: "unable to connect with ac97 modem"
date: 2004-11-27
forum: Hardware &amp; Laptops
---

### Post by mirons on 2004-11-27
Hi everybody. I installed ubuntu a week ago on an asus A4700L and I'm still fighting to get online. The integrated modem is an ac97 v92softmodem, from sis. In order to get it work i tried to use slmodemd ([http://www.smlink.com/main/down/slmodem-2.9.10.tar.gz](http://www.smlink.com/main/down/slmodem-2.9.10.tar.gz)). It makes wvdial get the hardware, but it still doesn't connect even using 'Carrier Check =  no' as suggested in the readme. Here is my wvdial.conf:

[Dialer Defaults]
Modem = /dev/ttySL0
Carrier Check = no
Baud = 460800
Init = ATZ
Dial Command = ATDT
Init1 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 ; This come from wvdialconf
Init2 = ATM1L3
Init3 = ATX3
ISDN = 0
Modem Type = Analog Modem

[Dialer ppp0]

Password = <mypass>
Phone = #########
Username = <myusername>


And wvdial output:

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATM1L3
ATM1L3
OK
--> Sending: ATX3
ATX3
OK
--> Modem initialized.
--> Sending: ATDT0332301010
--> Waiting for carrier.
ATDT0332301010
NO ANSWER
--> Unknown dial response string.
--> Disconnecting at Sat Nov 27 14:40:23 2004

The strange thing is I can't hear any sound from the modem, but wvdial seems communicating to it.
Thanks for the help!

---

### Post by az on 2004-11-27
It sounds like you have a pctel chipset modem.

Try scanModem from linmodems.org to see if you are using the correct driver.

---

### Post by mirons on 2004-11-27
According to scanModem and [http://linmodems.technion.ac.il/archive-fourth/msg02522.html](http://linmodems.technion.ac.il/archive-fourth/msg02522.html) the driver is right; I'm more and more convinced the trouble is wvdial waits for the server answer (I discovered the same thing happened also under win, until "wait for signal before dialling" option was disabled). The fact is wvdial "Carrier Check" options doesn't affect it. Do I need another dialer? What else can I do to override answer waiting?

---

