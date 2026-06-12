---
title: "vodafone 3g pcmcia card installation"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by sudhashen on 2005-05-15
Hello

I've trawled google on this and it seems some people have been successful in installing 3g cards and have written howto's on them - see [http://www.timberwolf.ukfsn.org/debian-orange-3g.html](http://www.timberwolf.ukfsn.org/debian-orange-3g.html) and [http://www.kuix.de/umts/vodafone/](http://www.kuix.de/umts/vodafone/) for eg.  But I'm scratching my head in vain at one part of the procedure where the card is detected and mapped to a path in /dev. Just to be sure about the pocedure, I confirmed vendor and product id via device manager  and did the modprobe usbserial command to redectect devices.  my /var/log/messages - syslog and dmesg give information that the card is detected but not what it is mapped to:

ohci_hcd 0000:01:00.0: NEC Corporation USB
PCI: Setting latency timer of device 0000:01:00.0 to 64
ohci_hcd 0000:01:00.0: irq 11, pci mem 0x10800000
ohci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 1 port detected
PCI: Enabling device 0000:01:00.1 (0000 -> 0002)
ACPI: PCI interrupt 0000:01:00.1[B] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:01:00.1: NEC Corporation USB (#2)
PCI: Setting latency timer of device 0000:01:00.1 to 64
ohci_hcd 0000:01:00.1: irq 11, pci mem 0x10801000
ohci_hcd 0000:01:00.1: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 1 port detected
usb 3-1: new full speed USB device using ohci_hcd and address 2

As messages say that the card is detected as a usb device, I hoped that I could through trial and error look at usb devices in /dev but aside from there being endless lists of tty** there is no directory usb nor ttyusb**!  aaaarggghhhh!

did a lspci -vv and no luck there - but confirmed that the card is detected and has all sorts of wonderful information about it except what i need.

I'm about to tear my hair off - I hope someone out there could help me figure out how to get this device recognised properly please.  I did all of this as root btw.

Many thanx. ](*,)

update : as i am of a company that sells these cards and various others, I tried the other cards available and it seems the Novatel/Merlin card has no problems - I can set up as per instructions.  However the Option Quad Band lite does not setup according to procedure - does not map to dev so have to carry on digging and begging at forums.   I think all the howto's on how to get this to work is on the Novatel card.

Now got option card working - nice guy at [www.pharscape.org](www.pharscape.org) has the procedure to get the vodafone cards to work(but these cards are just rebranded option cards) However found out that modprobe.conf does not exist in Hoary and /etc/modules has to edited instead.  Also needed to add Carrier Check = no in wvdial.conf to get my cards to work.

Hope this helps all who need it.Contact me if you need any pointers and I'll try to help.

---

