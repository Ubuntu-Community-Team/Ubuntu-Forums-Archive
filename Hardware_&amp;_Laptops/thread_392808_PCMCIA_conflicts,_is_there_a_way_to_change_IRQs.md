---
title: "PCMCIA conflicts, is there a way to change IRQs?"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by mlfrancis on 2007-03-24
Hello All, 
I'll try to make this fairly short.  I've got an old Dell CP laptop loaded with a command-line version of Ubuntu Edgy 6.10.  I've been using it as a print server (CUPS), scanner server (SANE), and here recently I decided to hang an external USB drive off of it.

Long story short, I've got a 3COM PCMCIA (Card bus really) network card that ties to IRQ 11.  Then i have a PCMCIA (also really card bus) to USB2 card.  The problem I have is if I try writing to the external drive (off the PCMCIA card) through the network.  It works for a little while and then dies.  

If I hang the drive off the built-in USB1.0 port, then I have no problems.  I also don't really seem to have problem getting through the network with the USB2 drive connected as long as I'm not doing both - network to drive or drive to network.

My IRQ list is looking like this:

           CPU0
  0:     552935          XT-PIC  timer
  1:       1324          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  7:          1          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:          1          XT-PIC  acpi
 11:     712541          XT-PIC  uhci_hcd:usb1, yenta, yenta, eth1, ohci_hcd:usb
2, ehci_hcd:usb3, ohci_hcd:usb4
 12:        746          XT-PIC  i8042
 14:       7075          XT-PIC  ide0
NMI:          0
LOC:          0
ERR:          0
MIS:          0

I'm suprised I don't have a problem running it off the USB1.0 port because it shows up as uhci_hcd:usb1 and the USB2 PCMCIA card shows up as 2,3, and 4.  My ethernet PCMCIA card is also hanging off IRQ 11.  There's no settings in the BIOS for me to manually do anything.

Is there anyway I can shuffle the IRQ's for one of these around or am I hosed because they are both going through the PCMCIA slot?

Any help would be appreciated, and MUCH thanks in advance.

Michael

--- Update:  Well, I think I proved it to myself.  I found another PCMCIA network card that is indeed PCMCIA and it loads at INQ 3.  This setup works fine, except that the network card is only a 10mbit.  I really need to get a 100 working.  Any pointers on dealing with IRQs on this thing would be greatly appreciated.

---

