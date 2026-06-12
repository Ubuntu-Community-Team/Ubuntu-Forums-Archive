---
title: "Hibernate issues HP tx2z"
date: 2010-02-06
forum: Hardware
---

### Post by MrStill on 2010-02-06
I am having some strange issues with hibernation on my laptop. First of all, suspend works fine. When I try to put my laptop to sleep, I get a usb device error which is too quick for me to read. Then my computer acts as if it is hibernating. When I press for restart, I get the splash screen informing me that my computer is waking up - which never happens. 

I am running Ubuntu 9.10 on an HP tx2. I have 4 GB of ram and almost 5 GB of swap space. As for the hardware issue, I can provide my usb device list:

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 1b96:0001 N-Trig Duosense Transparent Electromagnetic Digitizer
Bus 007 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:a104 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Any advice?

---

### Post by IcarusR on 2010-02-07
Is there any mention of this error in the logs or dmesg ?

---

### Post by MrStill on 2010-02-07
I looked through dmesg and a couple of other logs. I didn't find anything that I understood to be  an error message. But, I don't often read the error messages. After the kernel upgrade last night, I don't get this error message anymore. 

Still no return from hibernate though.

---

