---
title: "Need Modem Drivers..........."
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by subashk80 on 2008-02-23
HI.........i am using edubuntu..............i had fitted an external modem and i need the drivers for it!
In the accompanied CD i find drivers for Fedora, Suse etc........there is no drivers for ubuntu and those doen't fit for mine.........where shall i find the driver for mine!!  Help me plz..........

---

### Post by jskandhari on 2008-02-23
have you tried the synaptic package manager open it type it in search and if you feel like you have found what you want tick download REBOOT and then post again if it doesn't work

---

### Post by hyperair on 2008-02-23
Could you describe your modem? Also post the following outputs with your modem connected and switched on:```
lspci -nn
``````
lsusb
```

---

### Post by subashk80 on 2008-02-26
Hi, i had tried with the package manager but it doen't work,
When i used the lspci command i got the following o/p.......what shall i do??


[1002:437b] (rev 01)
00:14.3 ISA bridge 
[0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge 
[1002:4377] (rev 80)
00:14.4 PCI bridge 
[0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge 
[1002:4371] (rev 80)
01:05.0 VGA compatible controller 
[0300]: ATI Technologies Inc RC410 [Radeon Xpress 200] 
[1002:5a61]
02:02.0 Ethernet controller 
[0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ 
[10ec:8139] (rev 10)
02:03.0 Communication controller 
**[0780]: Agere Systems Unknown device [11c1:0620]**  (this is my MODEM)

---

