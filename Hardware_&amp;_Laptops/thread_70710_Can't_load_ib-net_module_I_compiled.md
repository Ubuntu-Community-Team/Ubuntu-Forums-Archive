---
title: "Can't load ib-net module I compiled"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by Skrewdriver on 2005-09-30
I'm trying to install the drivers for a iBurst wireless broadband PCMCIA card.
I downloaded the drivers from [http://sourceforge.net/projects/ibdriver/](http://sourceforge.net/projects/ibdriver/)
"make", and "sudo make install" went with no problems, but I can't get the modules to load.
```
mark@ubuntu:/etc/modprobe.d$ sudo modprobe ib-pcmcia
Password:
WARNING: Error inserting ib_net (/lib/modules/2.6.10-5-386/kernel/drivers/net/ib-net.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ib_pcmcia (/lib/modules/2.6.10-5-386/kernel/drivers/net/ib-pcmcia.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
There was no relevant errors in dmesg.
The output from /var/log/messages is:
```

localhost kernel ib_pcmcia: Unknown symbol ib_net_deregister
localhost kernel ib_pcmcia: Unknown symbol ib_net_register
localhost kernel ib_pcmcia: Unknown symbol ib_net_fill
localhost kernel ib_pcmcia: Unknown symbol ib_net_parse

```

The installation is Hoary (from the CD) on a IBM Thinkpad T21.
Any help would be much appreciated - hate having to use XP to access net!

---

### Post by LinuxRules on 2005-11-26
Seems like you have solved your problems with the PCMCIA drivers, as you have not posted since early this year.

Hopefully can you then possibly help with USB iBurst UT driver problem I've encoutered.

I downloaded the current iburst drivers (1.2.8 ) from SF and they compiled and installed without apparent problem (Hoary Hedghog 5.04 [2.6.10-5-386] on IBM Thinkpad T40)

root@ubuntu:~$ lsmod  | grep ib
ib_usb                  6276  0
ib_net                  9380  1 ib_usb
ibm_acpi               17780  0
usbcore               107384  5 ib_usb,usbhid,ehci_hcd,uhci_hcd

Unfortunately this is not the case once you connect the UT to the USB. It locks the keyboard & mouse solid !!!

It does not write anything to /var/log/messages but on a tty logged in as root, it coughs up this message :

root@ubuntu:~ uhci_hcd 0000:00:1d.1: host system error, PCI problems ?
uhci_hcd 0000:00:1d.1: host controller halted, very bad !

Don't think you get errors any clearer than that !!!

Any ideas how to fix this one ??? Did I overlook something ???

---

### Post by Skrewdriver on 2005-11-26
hmmm .. I did get the PCMCIA drivers [up and running]("http://ubuntuforums.org/showthread.php?t=90512"), but your problem sees a bit beyond my area of expertise.

Post a mesaage in the [sourceforge ibdriver help forum]("http://http://sourceforge.net/forum/forum.php?forum_id=466966"), the  developers are very good at providing support.

Let us know if you get a result.

---

