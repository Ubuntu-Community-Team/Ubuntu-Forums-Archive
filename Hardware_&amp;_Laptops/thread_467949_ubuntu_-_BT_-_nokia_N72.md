---
title: "ubuntu - BT - nokia N72"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by feedbee on 2007-06-08
I had Nokia 7610. I used GPRS both on a cable, and through BT (bluetooth). All has understood, all has adjusted in ubuntu, all was OK. That I had bought Nokia n72. On a cable all worked as well as with 7610 (i.e. &#1054;&#1050;). But on BT &#8211; it rejected to work fine (see below). And, in Windows with n72 all OK both on a cable and on BT. In ubuntu and fedora - cable &#1054;&#1050;, BT - failed. Has tried 3! Different adapters BT was tested, including hi-level Jabra. Doesn&#8217;t work.

In detail about a problem: Has adjusted phone as the modem on rfcomm0. I adjust connection. I create the modem on rfcomm0. I set a line of initialization (it through kppp; did also by handles through configs - too most). I press to interrogate the modem - there is an interrogation. All commands of interrogation writes ERROR (in Windows interrogation runs normally).

When I press to be connected, the modem returns "&#1054;&#1050;" only at 1 command: AT. All the others - answer ERROR. And therefore connection not connect. In what a problem - I can not understand.

---

### Post by feedbee on 2007-06-09
The answer was received [here (in russian)]("http://forum.ubuntu.ru/index.php?topic=9379.msg68267#msg68267").

The problem was in the channel set by rfcomm.conf for rfcomm0. 

**$sdptool browse**
[SIZE="1"]...
Service Name: Dial-Up Networking
Service RecHandle: 0x10081
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3
...[/SIZE]

So I changed /etc/bluetooth/rfcomm.conf
[SIZE="1"]#
# RFCOMM configuration file.
#

rfcomm0 {
        # Automatically bind the device at startup
        bind yes;

        # Bluetooth address of the device
        device 00:1A:89:B3:32:04;

        # RFCOMM channel for the connection
        channel [COLOR="Red"]1[/COLOR];

        # Description of the connection
        comment "N72";
}[/SIZE]

---

