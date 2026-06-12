---
title: "No wireless and sound on my new Dell"
date: 2010-02-10
forum: Hardware
---

### Post by janderpola on 2010-02-10
I´ve using Ubuntu for two years. Today i recived my new laptop, its a Dell Studio 1558 ([this one]("http://configure2.euro.dell.com/dellstore/config.aspx?b=&c=es&cs=esdhs1&kc=NRS15353&l=es&m_30=321942&oc=N0055803&rbc=N0055803&s=dhs")), and i installed Ubuntu. 

Everything works ok except sound and wireless. I don´t matter not having sound, but i just need wireless. 

My wifi card it´s a Intel Wireless 6200, but lspci says other...

Here´s the result of lspci:

> 00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Arrandale PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
02:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
04:00.0 Network controller: Intel Corporation Device 422c (rev 35)
07:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
07:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
07:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
07:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

What can i do?

---

### Post by d3mia7 on 2010-02-18
Unfortunately I can't tell what version or wireless card you're running, but try this:

```
sudo apt-get install linux-backport-modules-karmic
```

---

### Post by thepar on 2010-02-21
I have the same wireless card: 

Network controller: Intel Corporation Device 422c (rev 35)

and installing the package **linux-backport-modules-karmic-generic** solved the wireless problem.

---

### Post by digitalpbk on 2010-04-02
The same happens in Sony Vaio CW Series, there is sound, but no wireless. Installing the backports worked perfectly and got wireless connectivity in a reboot. Posted the same here [Sony Vaio CW Linux Wifi Drivers installation]("http://digitalpbk.com/ubuntu/install-wireless-wifi-drivers-linux-karmic-9.1-sony-vaio-cw")

---

### Post by rhernandez on 2010-04-11
I solved the sound issue by following this steps: [http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/) 

I hope you find it useful.

Renny Hernandez.

---

### Post by Aitaix on 2010-09-25
same problem, though it couldn't find the package. weak sauce.



```

aitaix@Elton:~$ sudo apt-get install linux-backport-modules-karmic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backport-modules-karmic
aitaix@Elton:~$ 

```

---

