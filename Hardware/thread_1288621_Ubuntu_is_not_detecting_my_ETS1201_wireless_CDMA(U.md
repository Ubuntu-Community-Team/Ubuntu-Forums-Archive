---
title: "Ubuntu is not detecting my ETS1201 wireless CDMA(USB) modem"
date: 2009-10-11
forum: Hardware
---

### Post by sreeyeshns on 2009-10-11
I'm using ubuntu 9.04. It is not detecting my ETS1201 wireless CDMA(USB) modem. 

I tried, wvdial. But the it is telling that "the device /dev/ttyUSB0 does not exists". I also tried lsusb /dev/ttyUSB*. But the result was again negetive. 

                 What should I do? Someone please help me...... Can I use mknod command to create the /dev/ttyUSB0 device file? If so how? how will I get the minor and major number of my modem? 

I'm a newbie in the world of Linux.

---

### Post by mo.reina on 2009-10-12
disconnect the usb modem and post the output of this command

```
lsusb
```

then connect it and post the output of the same command.

---

### Post by mo.reina on 2009-10-12
you can read the posts on this page, it seems others have had the same problem and have been able to solve it

[http://art.ubuntuforums.org/showthread.php?p=8086696]("http://art.ubuntuforums.org/showthread.php?p=8086696")

---

### Post by sreeyeshns on 2009-10-13
> **mo.reina said:**
> disconnect the usb modem and post the output of this command

```
lsusb
```

then connect it and post the output of the same command.

First of thank you very much for spending your valuable time for answering my question. I would like to let you know one more thing. When you are replaying to this thread, you are not helping only a single person, but a group electronics engineering students in my college and ,of course, others, using the same modem and having the same problem. Most of them are using Windows and want to switch to Linux(ubuntu). But, why they hesitate is due to this problem. If this thread finally finds a solution, I'm sure that the ubuntu community will again expand.

      Ok I'll come to the matter. I tried lsusb command before and after connecting the modem and the outputs are like this.

Before connecting

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0e5e:6622  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

After connecting

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 12d1:1010 Huawei Technologies Co., Ltd. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0e5e:6622  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Please reply :)

---

### Post by mo.reina on 2009-10-15
ok before we try the manual way try downloading the driver by huawei at
[http://www.bioticaindia.com/ets1201.html]("http://www.bioticaindia.com/ets1201.html")

---

### Post by sreeyeshns on 2009-10-15
> **mo.reina said:**
> ok before we try the manual way try downloading the driver by huawei at
[http://www.bioticaindia.com/ets1201.html]("http://www.bioticaindia.com/ets1201.html")

I tried that link. Registration(free) is required for downloading from that site. I've requested for registation, but the confirmation mail is yet to come. I'll report when it comes.(sorry for my poor english). thanks

---

### Post by sreeyeshns on 2009-11-03
I've tried ubuntu 9.10. The result is the same. Any expert there to help me?

---

