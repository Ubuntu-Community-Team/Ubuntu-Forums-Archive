---
title: "eagle usb problem..."
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by silent_scream on 2005-10-02
Hi everybody!
I have the sagem fast 800 adsl modem.
with synaptic manager i installed eagle usb ullities and data.
the installation is succesfull, so
in a console i type: 

geonik@ubuntu:~$ startadsl


Modem is not operational!
Check eaglestat result to know its state!

geonik@ubuntu:~$ eaglestat
eagle-usb status display
-------------------------------------------------------------
Driver version 2.3.2     Chipset: Eagle0
Vendor ID : 0x1110     Product ID : 0x9031   Rev: 0x200b
USB Bus : 004    USB Device : 002        Dbg mask: 0x0
Ethernet Interface : none
MAC: 00:60:4c:71:23:76
Tx Rate           0  Rx Rate           0
FEC               0  Margin            0  Atten             0 dB
VID-CPE           0  VID-CO            0  HEC               0
VPI               0  VCI               0  Delin          GOOD
Cells Tx          0  Cells Rx          0
Pkts Tx           0  Pkts Rx           0
OAM               0  Bad VPI           0  Bad CRC           0
Oversiz.          0

Modem waiting for driver response.
Please send DSP (eaglectrl -d)

geonik@ubuntu:~$ eaglectrl -d
Unknown option on line 27
Unknown option on line 28
Unknown option on line 29
Unknown option on line 30
Unknown option on line 31
Unknown option on line 32
Unable to send options to driver: Unknown error 512
geonik@ubuntu:~$


what should I do? what am I doing wrong? 
thanx for your time!

---

### Post by groblus on 2005-10-13
hi, although i'm using 5.10 (clean install, my first ubuntu) i've got the same problem and i havent got a clue what's wrong if you've found any solution please share it
thx

---

### Post by goomior on 2005-10-14
You may download .debs that fixes this from [this site](http://www.paczki-ubuntu.cba.pl/). If you want to fix this by yourself just download headers for your kernel, sources for eagle-usb and recompile the driver with kernel-package. Best regards.

P.S. Sorry for my English ;)

---

### Post by vinz on 2005-10-18
Could you explain me how to install your package?
(I use Ubuntu 5.10)

I've downloaded from your website the package [FONT="Courier New"]eagle-usb-modules-2.6.12-9-386_2.1.1-2+20051014-1_i386.deb[/FONT], and I've installed with the command
```

dpkg -i eagle-usb-modules-2.6.12-9-386_2.1.1-2+20051014-1_i386.deb
```

At the end, I hadn't have [FONT="Courier New"]eagleconfig, eaglestat, ...[/FONT], so I've installed with ```
apt.get install eagle-usb-data eagle-usb-utils
```

The problem persists. I have also tried to reinstall, at the end, your package, but don't work... :mad: 

Help me please, if I haven't an internet connection, I can't use Ubuntu as OS.

---

### Post by accleo on 2005-10-24
I have the same problem (same output) and I'm wondering what can I do... in Hoary did worked. Please some help!! :) We want to keep running that amazing OS!! Any guru? ;)

---

### Post by goomior on 2005-10-27
You should use the package equivalent for your "uname -r". Then install eagle-usb-utils and eagle-usb-data with:
```
sudo apt-get install eagle-usb-data eagle-usb-utils
```
not:
```
apt.get install eagle-usb-data eagle-usb-utils
```
It must work. You may also build package by yourself. HOWTO is [here](http://forum.ubuntu.pl/viewtopic.php?t=1494) (in Polish). Translation will be available soon.

---

