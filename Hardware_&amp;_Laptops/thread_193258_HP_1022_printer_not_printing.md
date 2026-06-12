---
title: "HP 1022 printer not printing"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by e*clipse on 2006-06-09
I am using an HP 1022 printer and it will not print a test page.

1)Setup, using the system>administration>printing>new printers  utility
2)The utility recognizes my printer> HP LaserJet 1022
3)I then select the driver > Hpijs (reccomended) -HPLIB 0.9.7 (suggested)

After naming the printer, it appears on my printer list.
If I try to print a test page, it hangs indefinitely.

In my attempts to get this working, I obtained these drivers from linuxprinting.org:

HP-LaserJet_1020-Foo2zjs.ppd
HP-LaserJet_1022-hpijs.ppd

I installed them (first the Foo2zjs.ppd)  - mistake :(  - then tried to correct things by installing the hpijs.ppd driver.

After the "installing driver" technique did not work, I tried following steps 1-3 again (several times, with a reboot thrown in and voodoo dance for good luck :rolleyes: )

The log (below) shows the printer and USB are connected.

[SIZE="1"]
arrogantbastard@blackbox:~$ sudo tail -f /var/log/messages
Jun  9 13:38:25 blackbox -- MARK --
Jun  9 13:58:25 blackbox -- MARK --
Jun  9 14:18:25 blackbox -- MARK --
Jun  9 14:38:25 blackbox -- MARK --
Jun  9 14:58:25 blackbox -- MARK --
Jun  9 15:18:25 blackbox -- MARK --
Jun  9 15:38:26 blackbox -- MARK --
Jun  9 15:49:26 blackbox kernel: [4306162.638000] drivers/usb/class/usblp.c: usb lp0: nonzero read/write bulk status received: -84
Jun  9 15:49:27 blackbox kernel: [4306162.797000] usb 2-2: USB disconnect, addre ss 2
Jun  9 15:49:29 blackbox kernel: [4306165.477000] drivers/usb/class/usblp.c: usb lp0: removed
Jun  9 15:50:32 blackbox kernel: [4306228.055000] usb 2-2: new full speed USB device using uhci_hcd and address 3
Jun  9 15:50:32 blackbox kernel: [4306228.189000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2C17


[4306162.638000] drivers/usb/class/usblp.c: usblp0: nonzero read/write bulk stat us received: -84
[4306162.797000] usb 2-2: USB disconnect, address 2
[4306165.477000] drivers/usb/class/usblp.c: usblp0: removed
[4306228.055000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[4306228.189000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer de v 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2C17


arrogantbastard@blackbox:~$ /usr/lib/cups/backend/hp
direct hp:/usb/HP_LaserJet_1022?device=/dev/usblp0 "HP HP_LaserJet_1022" "hp:/usb/HP_LaserJet_1022?dev ice=/dev/usblp0"
arrogantbastard@blackbox:~$

[/SIZE]

***edit***
I reviewed "eric1397's" post "HOW TO install HP printers for beginners"
The technique listed did not work, but I was able to find some more info:
1)  printer NOT recognized on LAN
Using the Synaptic Package Manager, I found:
2)  all hpijs files exist (I think) here is a list:
foomatic-db
foomatic-db-engine
foomatic-db-hpijs
hpijs
hplip
hplip-ppds
libijs-0.35

I also found (in hplip-ppds) that HP-Laserjet_1022-hpijs.ppd IS an installed file.

However, in usr/share/ppd/custom there are 2 files:
HP-Laserjet_1020foo2zjs.ppd
HP-Laserjet_1022hpijs.ppd

could these files be causing the problem?
If so, can you just delete them, or are they referred to in another file?
If that is not the problem, how can I get this to work?  :confused:

I've got to say, Installing the system was easy, but installing this printer reminds me of old DOS hell! ](*,)

---

### Post by muep on 2006-06-26
Has anyone got a 1022 working in Dapper? It used to work great in Breezy.

:(

---

### Post by meddle on 2006-08-29
Hi,

We have about 3 of these printers here, and have had some problems on breezy (have not tested dapper).

Go read :
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1022](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1022)

Alternative driver :
[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

From your post it looks like you are using it on a usb-1.2 hub

>>Jun 9 15:50:32 blackbox kernel: [4306228.055000] usb 2-2: new full speed USB device using uhci_hcd and address 3

Some people reported that some of their problems went away after placing the printer on a usb2 hub (using ehci_hcd module)

We also experience the "hang after paper-out" problem reported in the first link. Only thing to do is a power cycle.

Maybe it is related to the changelog entry from HPlib :

From : [http://hpinkjet.sourceforge.net/hplip_readme.html](http://hpinkjet.sourceforge.net/hplip_readme.html)
>>HPLIP 0.9.3
>>9. Fixed intermittent device hang problem with LJ 1010/1012/1015 in hp.c. >>These devices cannot handle in-band USB deviceid queries.

Two versions of printers.conf entries for cups (/etc/cups/printers.conf) that works for us are as follow :

<DefaultPrinter YourPrinter>
Info HP LaserJet 1022 hpijs
Location
DeviceURI usb:/dev/usb/lp0
State Stopped
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

Or

<DefaultPrinter YourPrinter>
Info HP (HPLIP) HP LaserJet 1022 hpijs
Location
DeviceURI hp:/usb/HP_LaserJet_1022?device=/dev/usb/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

Good luck

Dirko

---

