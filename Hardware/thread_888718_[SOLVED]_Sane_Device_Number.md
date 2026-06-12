---
title: "[SOLVED] Sane Device Number"
date: 2008-08-13
forum: Hardware
---

### Post by kingjere on 2008-08-13
I have a script that looks like this:
```

#!/bin/bash
scanimage --mode Gray -x 216 -y 280 --device-name 'net:192.168.0.9:epkowa:libusb:**001:003**' --source 'Automatic Document Feeder' --resolution 300 > /home/kingjere/supersecretdirectory/`date +%F_%R`

```

It works great except that the server running saned isn't always on and sometimes the scanner is listed as "net:192.168.0.9:epkowa:libusb:**001:002**" wich makes the script fail. Is there a way to make the scanner always have the same number?

---

### Post by kingjere on 2008-08-26
This was due to my own ignorance I guess. I realized just today that if I power on the scanner and start the server it is 001:002. If however I start the server and then power on the scanner it is listed as 001:003. I haven't the faintest clue why that is, but it is. Therefore I say this is solved.

---

