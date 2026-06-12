---
title: "Configuring PCI using pciutils"
date: 2009-11-29
forum: Hardware
---

### Post by aelorenzo on 2009-11-29
Hi all,

I am trying to pull up and down GPIO pins of a VIA AMOS 3000 using pcitools.

I ahve some information from the vendor. For instance, if I want to change GPIO3 state:

- GPIO PCI chipset device is at bus 0, device 17, function 0. So, I access it using setpci -s 00:11.0.
- I have to "Enable the control register" following VIA instructions, so I write 1 to the register Rx53, bit 7. I use setpci -s 00:11.0 53=80:80 (bits:mask).
- Then, I have to program the corresponding output register bit, Rx4D bit 7, to the desired state. I want to pull it down, low value, so: setpci -s 00:11.0 4D=00:80.

If I perform it, I have the registers with the written values (53 --> 80 and 4D --> 00), something strange, because I thought that only the bit enabled by the mask was allowed to be changed.

Also, the GPIO3 pin has all the time 5.0 volts, so I suppose that it is at high state and I am not able to change it!

Any help plz?

---

