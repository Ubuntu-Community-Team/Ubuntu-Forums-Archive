---
title: "Can I do Ubuntu-to-Ubuntu transfers with a USB 2.0 cable ?"
date: 2011-03-29
forum: Hardware
---

### Post by KewlEugene on 2011-03-29
Can I do Ubuntu-to-Ubuntu transfers with a USB 2.0 cable ?

Like with the Dynex USB 2.0 File Transfer Adapter PC cable or Encore 1.8 m PC to PC File USB2.0/USB1.1 Transfer Cable ?

---

### Post by dandnsmith on 2011-03-29
Interesting question - after a limited amount of googling, I'm tempted to say no (because they all quote Windows versions to do the transfer, suggesting some additional software is needed).

If you could set up usb-usb LAN connection, and used a usb cable with suitable crossover of the data in/out pairs, it would be feasible - but I've not come across anyone doing it.

My workaround is a transfer using external HDD or USBstick. There was a time when people were cross-connecting using serial ports (quite easy) or parallel ports (tricky to get it working, and not all parallel ports would support it).

Do you have ethernet ports or firewire ports?

Sorry

---

### Post by KewlEugene on 2011-04-01
Anything is possible, but which would be the fastest to transfer 1TB of data per day ? 802.11n ? USB 2.0 ? I don't have firewire.

---

### Post by dandnsmith on 2011-04-01
802.11n theoretical with 2 wifi channels 300Mbps
USB2.0 theoretical on its own 480Mbps

Allowing for protocol framing etc, the wifi may only reach 130-150Mbps
Not sure if there are comparable overheads for USB2.0

Don't forget that this is bits not bytes, so you have to divide by as much as 12 to get transfer rate in Bytes.

HTH

---

### Post by oldfred on 2011-04-01
If the two computers are close enough to use USB, why not Ethernet?

You can use standard cables if you have a router, some newer ports even let you use standard cables with a direct connection. Or you can create a crossover cable for a direct connection. But for the cost of a cross over cable you can buy a hub. But I would suggest a router. 

If you have wifi do not not have a router already? 

I did have to use a $5 USB to Ethernet converter on my 10 year old laptop to make it work with Ethernet. It only has one USB port, but worked just fine with the converter.

---

### Post by KewlEugene on 2011-04-03
We all know everything is possible and with enough time we can all try them  then figure it out and name the fastest alternative. But who has tried it already and worked out the numbers for the fastest Ubuntu to Ubuntu transfer ? Is there a link to an article ?

---

### Post by dandnsmith on 2011-04-03
That's a good question. You might find an article on techniques and methods, but any timing is going to depend on local conditions (speed of ethernet, size of stuff to transfer, speed of ethernet-usb ...)

---

### Post by oldfred on 2011-04-03
Theoretical maximums do not mean much but:

Ethernet speeds:
[http://www.homenethelp.com/web/explain/about-network-speeds.asp](http://www.homenethelp.com/web/explain/about-network-speeds.asp)
10Mbps     10 X 1,000,000 bits per second = 10 million one's or zero's
or     1,250,000 bytes/sec

[http://en.wikipedia.org/wiki/USB2](http://en.wikipedia.org/wiki/USB2)
The theoretical maximum data rate in USB 2.0 is 480 Mbit/s (60 MB/s) per controller
[http://en.wikipedia.org/wiki/USB3#USB_3.0](http://en.wikipedia.org/wiki/USB3#USB_3.0)
SuperSpeed (USB 3.0) rate of 4800 Mbit/s (~572 MB/s).
But speeds are more limited by devices at each end.

---

### Post by SeijiSensei on 2011-04-03
> **KewlEugene said:**
> We all know everything is possible and with enough time we can all try them  then figure it out and name the fastest alternative. But who has tried it already and worked out the numbers for the fastest Ubuntu to Ubuntu transfer ? Is there a link to an article ?

I doubt anything would beat 1000BaseT ("gigabit") Ethernet.

---

