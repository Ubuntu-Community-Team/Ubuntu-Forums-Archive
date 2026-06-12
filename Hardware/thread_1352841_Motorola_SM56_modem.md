---
title: "Motorola SM56 modem"
date: 2009-12-12
forum: Hardware
---

### Post by aran-p on 2009-12-12
I have a Motorola SM56 Internal modem (PCI).
OS Linux Ubuntu 9.10

I have a problem in getting my modem to work.
I followed the instructions on [http://ubuntuforums.org/showthread.php?t=460331&highlight=linmodems](http://ubuntuforums.org/showthread.php?t=460331&highlight=linmodems)
but got the reply that Kernel has changed and this solution doesn't work with Ubuntu 9.10.

Today I found new instructions in:  [http://www.linuxforums.org/articles/how-to-connect-a-dial-up-modem-in-ubuntu-9_509.html](http://www.linuxforums.org/articles/how-to-connect-a-dial-up-modem-in-ubuntu-9_509.html)
But the modem still doesn't work.
Can anyone help?
Thanks

---

### Post by IcarusR on 2009-12-12
We need more info....

How far do you get ? (at what point does it fail/not work)
What errors do you get ?
Is there anything pertinent in syslog ?

---

### Post by aran-p on 2009-12-12
Does this help:

aran@aran-desktop:~$ sudo cp -vp /etc/wvdial.conf /etc/wvdial.conf.1
[sudo] password for aran: 
`/etc/wvdial.conf' -> `/etc/wvdial.conf.1'
aran@aran-desktop:~$ sudo cp -vp /etc/wvdial.conf /etc/wvdial.conf.1
`/etc/wvdial.conf' -> `/etc/wvdial.conf.1'
aran@aran-desktop:~$ sudo wvdialconf 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
aran@aran-desktop:~$ sudo modprobe cdc_acm
aran@aran-desktop:~$ ls -l /dev/tty*
crw-rw-rw- 1 root tty     5,  0 2009-12-09 07:34 /dev/tty
crw--w---- 1 root root    4,  0 2009-12-09 06:51 /dev/tty0
crw------- 1 root root    4,  1 2009-12-09 06:51 /dev/tty1
crw--w---- 1 root tty     4, 10 2009-12-09 06:51 /dev/tty10
crw--w---- 1 root tty     4, 11 2009-12-09 06:51 /dev/tty11
crw--w---- 1 root tty     4, 12 2009-12-09 06:51 /dev/tty12
crw--w---- 1 root tty     4, 13 2009-12-09 06:51 /dev/tty13
crw--w---- 1 root tty     4, 14 2009-12-09 06:51 /dev/tty14
crw--w---- 1 root tty     4, 15 2009-12-09 06:51 /dev/tty15
crw--w---- 1 root tty     4, 16 2009-12-09 06:51 /dev/tty16
crw--w---- 1 root tty     4, 17 2009-12-09 06:51 /dev/tty17
crw--w---- 1 root tty     4, 18 2009-12-09 06:51 /dev/tty18
crw--w---- 1 root tty     4, 19 2009-12-09 06:51 /dev/tty19
crw------- 1 root root    4,  2 2009-12-09 06:51 /dev/tty2
crw--w---- 1 root tty     4, 20 2009-12-09 06:51 /dev/tty20
crw--w---- 1 root tty     4, 21 2009-12-09 06:51 /dev/tty21
crw--w---- 1 root tty     4, 22 2009-12-09 06:51 /dev/tty22
crw--w---- 1 root tty     4, 23 2009-12-09 06:51 /dev/tty23
crw--w---- 1 root tty     4, 24 2009-12-09 06:51 /dev/tty24
crw--w---- 1 root tty     4, 25 2009-12-09 06:51 /dev/tty25
crw--w---- 1 root tty     4, 26 2009-12-09 06:51 /dev/tty26
crw--w---- 1 root tty     4, 27 2009-12-09 06:51 /dev/tty27
crw--w---- 1 root tty     4, 28 2009-12-09 06:51 /dev/tty28
crw--w---- 1 root tty     4, 29 2009-12-09 06:51 /dev/tty29
crw------- 1 root root    4,  3 2009-12-09 06:51 /dev/tty3
crw--w---- 1 root tty     4, 30 2009-12-09 06:51 /dev/tty30
crw--w---- 1 root tty     4, 31 2009-12-09 06:51 /dev/tty31
crw--w---- 1 root tty     4, 32 2009-12-09 06:51 /dev/tty32
crw--w---- 1 root tty     4, 33 2009-12-09 06:51 /dev/tty33
crw--w---- 1 root tty     4, 34 2009-12-09 06:51 /dev/tty34
crw--w---- 1 root tty     4, 35 2009-12-09 06:51 /dev/tty35
crw--w---- 1 root tty     4, 36 2009-12-09 06:51 /dev/tty36
crw--w---- 1 root tty     4, 37 2009-12-09 06:51 /dev/tty37
crw--w---- 1 root tty     4, 38 2009-12-09 06:51 /dev/tty38
crw--w---- 1 root tty     4, 39 2009-12-09 06:51 /dev/tty39
crw------- 1 root root    4,  4 2009-12-09 06:51 /dev/tty4
crw--w---- 1 root tty     4, 40 2009-12-09 06:51 /dev/tty40
crw--w---- 1 root tty     4, 41 2009-12-09 06:51 /dev/tty41
crw--w---- 1 root tty     4, 42 2009-12-09 06:51 /dev/tty42
crw--w---- 1 root tty     4, 43 2009-12-09 06:51 /dev/tty43
crw--w---- 1 root tty     4, 44 2009-12-09 06:51 /dev/tty44
crw--w---- 1 root tty     4, 45 2009-12-09 06:51 /dev/tty45
crw--w---- 1 root tty     4, 46 2009-12-09 06:51 /dev/tty46
crw--w---- 1 root tty     4, 47 2009-12-09 06:51 /dev/tty47
crw--w---- 1 root tty     4, 48 2009-12-09 06:51 /dev/tty48
crw--w---- 1 root tty     4, 49 2009-12-09 06:51 /dev/tty49
crw------- 1 root root    4,  5 2009-12-09 06:51 /dev/tty5
crw--w---- 1 root tty     4, 50 2009-12-09 06:51 /dev/tty50
crw--w---- 1 root tty     4, 51 2009-12-09 06:51 /dev/tty51
crw--w---- 1 root tty     4, 52 2009-12-09 06:51 /dev/tty52
crw--w---- 1 root tty     4, 53 2009-12-09 06:51 /dev/tty53
crw--w---- 1 root tty     4, 54 2009-12-09 06:51 /dev/tty54
crw--w---- 1 root tty     4, 55 2009-12-09 06:51 /dev/tty55
crw--w---- 1 root tty     4, 56 2009-12-09 06:51 /dev/tty56
crw--w---- 1 root tty     4, 57 2009-12-09 06:51 /dev/tty57
crw--w---- 1 root tty     4, 58 2009-12-09 06:51 /dev/tty58
crw--w---- 1 root tty     4, 59 2009-12-09 06:51 /dev/tty59
crw------- 1 root root    4,  6 2009-12-09 06:51 /dev/tty6
crw--w---- 1 root tty     4, 60 2009-12-09 06:51 /dev/tty60
crw--w---- 1 root tty     4, 61 2009-12-09 06:51 /dev/tty61
crw--w---- 1 root tty     4, 62 2009-12-09 06:51 /dev/tty62
crw--w---- 1 root tty     4, 63 2009-12-09 06:51 /dev/tty63
crw--w---- 1 root root    4,  7 2009-12-09 06:51 /dev/tty7
crw--w---- 1 root tty     4,  8 2009-12-09 06:51 /dev/tty8
crw--w---- 1 root tty     4,  9 2009-12-09 06:51 /dev/tty9
crw-rw---- 1 root dialout 4, 64 2009-12-09 07:36 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-12-09 07:36 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-12-09 07:36 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-12-09 07:36 /dev/ttyS3
aran@aran-desktop:~$

---

### Post by aran-p on 2009-12-12
This is my modemscan results

For candidate card in slot 00:09.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:09.0	1057:3052	1057:3020	Modem: Motorola SM56 Data Fax Modem 

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 00:09.0 ----
pci 0000:00:09.0: reg 10 32bit mmio: [0xfdfff000-0xfdffffff]
pci 0000:00:09.0: reg 14 io port: [0xfc00-0xfcff]
pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
pci 0000:00:09.0: PME# disabled
serial 0000:00:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
0000:00:09.0: ttyS2 at I/O 0xfc08 (irq = 18) is a 16450
0000:00:09.0: ttyS3 at I/O 0xfc10 (irq = 18) is a 8250
Couldn't register serial port 0000:00:09.0: -28

 The PCI slot 00:09.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:09.0:
	Modem chipset  detected on
NAME="Modem: Motorola SM56 Data Fax Modem "
CLASS=0703
PCIDEV=1057:3052
SUBSYS=1057:3020
IRQ=18
IDENT=slamr

---

