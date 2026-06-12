---
title: "Finding serial/COM Ports in Ubuntu"
date: 2014-09-17
forum: Hardware
---

### Post by sumankumar on 2014-09-17
Dear experts,

Happy morning!!!

Our requirement is to connect multiple devices to a system and the data from devices will be captured by our custom built application. This we have achieved in Windows machine by reading the virtual COM ports successfully. Now we would like to do this in the Ubuntu machine, our challenge is to read the COM ports in Ubuntu and once we get them, will place them in the configuration file and our application takes care of the remaining procedure. 

Please suggest us the approach. 

Thanks in advance.

Best Regards,

Kumar

---

### Post by sumankumar on 2014-09-17
Hi Experts, waiting for your reply.

---

### Post by slickymaster on 2014-09-17
There's **setserial** which is a program designed to set and/or report the configuration information associated with a serial port. This information includes what I/O port and IRQ a particular serial port is using, and whether or not the break key should be interpreted as the Secure Attention Key, and so on.

Please refer to [http://manpages.ubuntu.com/manpages/precise/man8/setserial.8.html](http://manpages.ubuntu.com/manpages/precise/man8/setserial.8.html)

---

### Post by sandyd on 2014-09-17
Thread moved to the Hardware forums

---

