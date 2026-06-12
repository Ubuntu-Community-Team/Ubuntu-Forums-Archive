---
title: "Internal serial ports not working with standard IRQ"
date: 2015-02-09
forum: Hardware
---

### Post by Craig_Richards on 2015-02-09
Hi,

I have recently set up a unit with Ubuntu and i am trying to use the internal serial ports to interface with another piece of hardware in the system. The problem is that i am unable to read or write to the serial port when it's using its standard IRQ (by default it uses IRQ 7). If i use setserial to set the IRQ to 0 it works but is pretty inefficient and seems to be causing issues with the other piece of hardware.

The other piece of hardware is a board which, among other things, passes the signal from a GPS antenna to the motherboard. On an older motherboard this worked fine but when i'm using IRQ 0 on the ports to get them working i experience very high jitter when using NTP, between 5 and 10ms. I'm assuming this is because of the serial ports using the timer IRQ, feel free to correct me on that.

I have tried to read them using cat and i am unable to write to them with echo. Trying to write to any of the onboard serial ports results in the terminal hanging for 30 seconds. I have verified that it isn't the hardware at fault as i have 5 other identical motherboards which all do the same.

What would the reason be for the serial ports not working using their  standard IRQ? The serial controller is a Fintek F81866 and has the IRQs  set to Auto in the bios which flicks them onto 7.

I'm hoping somebody can shed some light on this as it's been annoying me for some time and i'm all out of ideas now.

---

