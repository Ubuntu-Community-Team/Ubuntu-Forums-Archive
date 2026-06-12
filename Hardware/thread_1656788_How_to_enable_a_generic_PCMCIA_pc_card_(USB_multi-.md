---
title: "How to enable a generic PCMCIA pc card (USB multi-ports)"
date: 2010-12-31
forum: Hardware
---

### Post by nEoTeChMaN on 2010-12-31
Hi all,

I just bought a generic PCMCIA pc card (4-ports USB) and how do I enable it?

Using Xubuntu 10.10 by the way on a PIII 1.2GHz, 1GB RAM and 60GB HD

---

### Post by nEoTeChMaN on 2010-12-31
Bump...

Any suggestions?

---

### Post by IcarusR on 2010-12-31
First please do not bump a thread for at least a day to give folks a chance to read & reply.

It should just work, have you tried it ?

Check that the system recognises the card by removing it & waiting a minute, then reinsert card. 
Now in a terminal type

```
dmesg | tail -n 20
```

You should see 20 lines in the terminal, if the card is recognised there should be mention of the card being inserted followed by more details.

>  pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0

---

### Post by nEoTeChMaN on 2011-01-01
neo@neo-eveshamvale:~$ dmesg | tail -n 20
[ 2059.402927] uhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 4
[ 2059.402988] uhci_hcd 0000:02:00.0: irq 10, io base 0x0000b000
[ 2059.403669] hub 4-0:1.0: USB hub found
[ 2059.403689] hub 4-0:1.0: 2 ports detected
[ 2059.406739] uhci_hcd 0000:02:00.1: enabling device (0000 -> 0003)
[ 2059.406772] uhci_hcd 0000:02:00.1: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[ 2059.406809] uhci_hcd 0000:02:00.1: UHCI Host Controller
[ 2059.407236] uhci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 5
[ 2059.407300] uhci_hcd 0000:02:00.1: irq 10, io base 0x0000b020
[ 2059.407986] hub 5-0:1.0: USB hub found
[ 2059.408088] hub 5-0:1.0: 2 ports detected
[ 2059.409561] ehci_hcd 0000:02:00.2: enabling device (0000 -> 0002)
[ 2059.409591] ehci_hcd 0000:02:00.2: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[ 2059.409644] ehci_hcd 0000:02:00.2: EHCI Host Controller
[ 2059.410145] ehci_hcd 0000:02:00.2: new USB bus registered, assigned bus number 6
[ 2059.410250] ehci_hcd 0000:02:00.2: irq 10, io mem 0x2c000200
[ 2059.426759] ehci_hcd 0000:02:00.2: USB 2.0 started, EHCI 1.00
[ 2059.427716] hub 6-0:1.0: USB hub found
[ 2059.427737] hub 6-0:1.0: 4 ports detected
[ 2060.368791] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 178
neo@neo-eveshamvale:~$ 

When I plugged in a USB mouse or whatever nothing happened.

---

### Post by IcarusR on 2011-01-01
> [ 2059.427737] hub 6-0:1.0: 4 ports detected

Ubuntu sees the card.

Unplug & then replug in usb device & check for it in output of dmesg.

```
dmesg | tail -n 20
```

Or

```
lsusb
```

---

### Post by nEoTeChMaN on 2011-01-04
Same as above. 

Should it be any different? Just because the system detected the device doesn't means I can use it. It won't even pick up as simple as a USB mouse.

---

### Post by Fafler on 2011-01-04
IcarusR wanted you to run the dmesg command after connecting a USB device to the card, not the card itself. The output of lsusb is still useful for us.

---

### Post by nEoTeChMaN on 2011-01-05
Sorry. I misunderstood the statement.

Will add a device now.

---

### Post by nEoTeChMaN on 2011-01-05
The result is the same.

---

### Post by Fafler on 2011-01-06
Weird. I think you should try it out on another laptop if you possibly can. The card is detected correctly and this kind of hardware rarely cause any hardware problems.

It could also be some kind of power issue, where the laptop doesn't deliver enough juice for the card to function.

---

