---
title: "How can I define a SPD_WARP setserial flag, using a UDEV rule?"
date: 2007-02-23
forum: Hardware &amp; Laptops
---

### Post by Carlos Santiago on 2007-02-23
Hi. I need to set a SPD_WARP flag to my PCMCIA modem, in order to use the full bandwidth. 
Manually I do it with:

$setserial /dev/ttyS0 low_latency spd_warp

And it works fine, despite the conflicts with other serial devices.
Thus, in order to avoid these conflicts I need to use pcmciautils (my kernel is above 2.6.13) with udev. But ...
How can I set the SPD_WART and LOW_LATENCY flags to the device, inside the UDEV rule?

Thank you in advance

Carlos

---

### Post by Carlos Santiago on 2007-02-23
I have already tried all this options with no success:
ACTION=="add" KERNEL=="ttyS0" NAME+="modem" PROGRAM+="/usr/bin/setserial %k low_latency spd_warp"
ACTION=="add" KERNEL=="ttyS0" NAME+="modem" PROGRAM+="/usr/bin/setserial /dev/%k low_latency spd_warp"
ACTION=="add" KERNEL=="ttyS0" NAME+="modem" RUN+="/usr/bin/setserial %k low_latency spd_warp"
ACTION=="add" KERNEL=="ttyS0" NAME+="modem" RUN+="/usr/bin/setserial /dev/%k low_latency spd_warp"

Moreover, I would like to know if it is possible to circumvent the usage of setserial.

Thanx again

Carlos

---

### Post by Carlos Santiago on 2007-02-26
I will try to clarify my problem, and also helping someone that has similar problems.
I use an Updated Ubuntu 6.06, and my kernel is above 2.6.13.
As it is documented, the service /etc/init.d/pcmcia is no longer available for kernels above 2.6.13.
I must switch to /etc/init.d/pcmciautils that uses udev (see man udev)

UDEV allows you to define rules that will be used when an hardware is found. 

The rules are files located in the folder /etc/udev/rules.d/ with the suffix .rules
Each rule is one line, where '==' makes an evaluation, and '+=' assign an action.

For example:
ACTION=="add" KERNEL=="ttyS0" NAME+="modem" RUN+="/usr/bin/setserial %k low_latency spd_warp"
mean that when a piece of hardware is found (ACTION=="add") with device /dev/ttyS0 (KERNEL=="ttyS0"), it is changed to /dev/modem (NAME+="modem"), and the setserial command is executed with low_latency and spd_warp parameters (RUN+="/usr/bin/setserial %k low_latency spd_warp")

Everything works unless the setserial command, that I must execute by hand.

---

