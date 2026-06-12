---
title: "problem with 56k serial model"
date: 2010-10-28
forum: Hardware
---

### Post by sebastien_gd on 2010-10-28
I am trying to use a 56k modem with ubuntu . The modem is an external serial modem "3com us robotics 56 k fax modem".
When I send echo atdt3333333 > /dev/ttyS1, I can see lights flashing.


But wvdialconf failed. Hthe outptu of wvdialconf is the following:
Scanning your serial ports for a modem.

[I]ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- 
ttyS1<*1>: failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- 
ttyS1<*1>: and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?[/I]


Does anyone can help me?

Thanks

---

