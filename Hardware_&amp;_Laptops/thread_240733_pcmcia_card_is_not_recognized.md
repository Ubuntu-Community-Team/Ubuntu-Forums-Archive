---
title: "pcmcia card is not recognized"
date: 2006-08-21
forum: Hardware &amp; Laptops
---

### Post by armino on 2006-08-21
Hi!

I tried to install a wlan card when I realized that the pcmcia card is not recognized. I have ubuntu 6.06 running on a SONY VAIO PCG-FX170.

I copied the relevant part of the dmesg file here: 

[42.043462] PCI: No IRQ known for interrupt pin B of device0000:01:02.1.
[42.043500] Yenta: CardBus bridge found at 0000:01:02.1 [104d:80df]
[42.043527] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[42.043531] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.


Any help in making it work would be very much appreciated!

Thanks!

Armin

---

### Post by encompass on 2006-08-21
did you check your bios?  is it disabled like it says there?

---

### Post by armino on 2006-08-22
Hi!

Thanks for the quick reply!
The pcmcia card is working on windows, so I do not think that this is the problem.

Armin

---

### Post by encompass on 2006-08-22
Is your system upto date.  Make sure of that too... My PCMCIA card did not work at first with dapper until I had updated my system.
Sounds weird but in your bios... disble you printer and serial ports and tell me if you see anything from this..
```
cardctl status
```
anything?
put the card in and see if you see your card... you should get something like this...
```
encompass@lappy:~$ cardctl status
Socket 0:
  no card
Socket 1:
  5V 16-bit PC Card
  function 0: [ready]
encompass@lappy:~$

```

---

### Post by armino on 2006-08-22
I updated my system and disabled the serial and parallel port in the BIOS.

When running 'cardctl status' I get:
Socket 0:
  no card
Socket 1:
  no card

:(

---

### Post by encompass on 2006-08-22
Stumped sorry...

---

### Post by armino on 2006-08-22
Thanks anyway!

---

