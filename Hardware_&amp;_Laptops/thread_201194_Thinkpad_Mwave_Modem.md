---
title: "Thinkpad Mwave Modem"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by kebajonathan on 2006-06-21
Hey Guys,

I know there are some guys using Thinkpad 600/600E/600X notebooks. Have you set up your Mwave modem?
If so, could you give me the directions?
What I've done so far:

1) Added this line to /etc/modprobe.d/options:
```
 options mwave mwave_3780i_irq=10 mwave_3780i_io=0x0130 mwave_uart_irq=3 mwave_uart_io=0x2f8 
```

2) Added these lines to /etc/pcmcia/config.opts:
```
 exclude irq 3
exclude irq 10 
```

3) execute:
```
sudo apt-get install setserial
```

4) using ```
sudo gedit /usr/local/etc/mwavem.conf
```
to change ```
DEVICE=/dev/modems/mwave
``` to ```
DEVICE=/dev/mwave
```

5) reboot

6) execute:
```
sudo setserial /dev/ttyS1 autoconfig
mwavem
```

7) Now, setting up vwdial, using ```
wvdialconf /etc/wvdial.conf
```
I get this:
```
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0
WvModem<*1>: Cannot set information for serial port.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   S4   S5   S6   S7   S8
Modem Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
Modem Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
Modem Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
Modem Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
Modem Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

```

What can I do? What did I do wrong?

I got it from [http://forums.gentoo.org/viewtopic-t-269527-highlight-600e+mwave.html](http://forums.gentoo.org/viewtopic-t-269527-highlight-600e+mwave.html) since I didn't find anything here...

If you are looking for a howto on sound and PCMCIA for the 600E, try this: [http://www.mueller.ch.vu/misc/tp600e_en.html]("http://www.mueller.ch.vu/misc/tp600e_en.html").

---

### Post by kebajonathan on 2006-06-21
Isn't there anyone who knows?

---

### Post by kebajonathan on 2006-06-23
Wuhuuu!

I got it to work!
just read [http://www.mueller.ch.vu/misc/tp600e_en.html]("http://www.mueller.ch.vu/misc/tp600e_en.html") and you should get it to work too.

---

