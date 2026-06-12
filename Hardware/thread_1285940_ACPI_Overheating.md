---
title: "ACPI Overheating"
date: 2009-10-08
forum: Hardware
---

### Post by Maintech on 2009-10-08
I have an issue with the computer thinking it is overheating when it isn't. I have a Vendetta CPU cooler on my processor and all the latest bios updates. I have lmsensors installed and run conkey with my cpu temps displayed at all times. My issue lies with "Temp1" which the computer sees as my processor. My 4 cores will be showing between 25 and 30C and temp1 will show about 37. With the computer idled down to 2ghz and no running programs (only background processes) my temp1 will suddenly shoot up to 121C while the individual processors will show no change. After a few minutes the computer shuts down. My log shows this:
Oct  8 07:38:35 quad kernel: [65453.637618] ACPI: Critical trip point

Oct  8 07:38:35 quad kernel: [65453.639075] ACPI: Unable to turn cooling device [ffff88012f81a820] 'on'

Oct  8 07:38:40 quad bonobo-activation-server (me-1855): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Hjm1bM5BPg: Connection refused

Oct  8 07:38:41 quad kernel: [65459.836143] ACPI: Critical trip point

Oct  8 07:38:41 quad kernel: [65459.836176] ACPI: Unable to turn cooling device [ffff88012f81a820] 'on'

Oct  8 07:38:43 quad exiting on signal 15

I am attaching a file with more hardware info. I hope I have included everything needed to determine what is causing my issue. I have 2 case fans that are not attached to the motherboard but the case is cool. I can do a fast reboot and temp1 is back to the correct temp.

---

### Post by TheStroj on 2009-10-08
```
 Unable to turn cooling device [ffff88012f81a820] 'on'
```

Sounds like fan isn't working, or OS can't turn it on.

---

### Post by Maintech on 2009-10-08
> **TheStroj said:**
> ```
 Unable to turn cooling device [ffff88012f81a820] 'on'
```

Sounds like fan isn't working, or OS can't turn it on.

There is only one fan attached to the motherboard. The cpu fan. It is the Vendetta cpu cooler. The issue isn't so much that it can't find a fan to turn on as it is that it sees 121C as the CPU temp when it isn't. I am unable to determine why the temp seen on "Temp1" which is an ACPI monitored temperature will suddenly go from 37C to 121C in less than 1 second and no other temps change. None of the core temps rise. It seems that there is an issue with ACPI.

---

### Post by Maintech on 2009-10-08
<Bump>

Surely someone has an answer...or a request for some specific information. There has to be a fix for this. If nothing else, a way to turn "Temp1" off.

---

### Post by Yellow Pasque on 2009-10-08
Try setting the critical trip point to 0 if you're sure that your system isn't overheating: [http://www.columbia.edu/~ariel/acpi/acpi_howto.html#trip_points](http://www.columbia.edu/~ariel/acpi/acpi_howto.html#trip_points)

I guess you could have a faulty BIOS, or maybe it's a bug in lm-sensors.

Off-topic: please post plain text instead of OpenOffice documents (text editors load much faster than OO :) )

---

### Post by Maintech on 2009-10-09
>  	
Re: ACPI Overheating
Try setting the critical trip point to 0 if you're sure that your system isn't overheating: [http://www.columbia.edu/~ariel/acpi/...ml#trip_points](http://www.columbia.edu/~ariel/acpi/...ml#trip_points)

I guess you could have a faulty BIOS, or maybe it's a bug in lm-sensors.

Off-topic: please post plain text instead of OpenOffice documents (text editors load much faster than OO ) 

Good article and thank you for the suggestion. I found my polling was turned off so I turned it on and will try that before moving on to changing other settings. I can't make up my mind if the issue is a faulty motherboard temp sensor or ACPI. It may work fine for several days then suddenly have a temp spike of 121C and shut down....and it under no load at the time. I am hoping that the polling will end that.

I will also remember to post using plain text next time :P

---

