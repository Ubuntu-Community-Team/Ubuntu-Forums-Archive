---
title: "US Robotics external modem for faxing"
date: 2010-12-06
forum: Hardware
---

### Post by gizmobay on 2010-12-06
I have a PCI fax/modem but the drivers don't work for 10.10 64 bit. I could run under 32 bit pci passthrough but I don't want to flash my Mobo BIOS. I think I'll just buy an external US Robotics. Does anyone know if the .v92 usb works under 10.10 or should I go with serial? I'm also open to other brands external. Thanks

---

### Post by Fafler on 2010-12-07
Unlike those annoying PCI cards, the USB devices should as far as i know all be "full" modems and not need any more drivers than the USB to serial converter the modem uses itself. Just buy any ol' USB modem. Or a USB to RS232 converter and a even older modem.

The PCI cards are often more like sound cards. They take care of the part of converting the PSTN input to analog audio data and uses the host CPU and driver to read the data stream. External modems have a chip for that, and are a lot less complex to mess around with.

---

### Post by gizmobay on 2010-12-07
Thanks for the help. Would even something like this work or am I pushing my luck ;)

[http://tinyurl.com/2f8y7zo](http://tinyurl.com/2f8y7zo)

---

### Post by dandnsmith on 2010-12-07
Hope the little black box really is a fax-modem.

I note that the caption says PCI Fax Modem, which isn't in accord with the pic.

---

### Post by IcarusR on 2010-12-07
You'd be better buying a standard external modem, U S Robotics or Pace. The modem you linked maybe a software modem & be difficult to setup under ubuntu.

---

