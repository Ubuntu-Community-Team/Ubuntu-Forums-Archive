---
title: "Intel NUC (BOXD34010WYK2) ir issues"
date: 2014-08-17
forum: Hardware
---

### Post by Jaman42 on 2014-08-17
Hi,
I am running Ubuntu 14.04 and trying to get my remote set up with lirc. I got the hardware.conf & lircd.conf all set up and working, I mapped the keys so that XBMC understands the keys being pressed and everything is working fine except one thing.

Not sure what is happening but it seems like my ir reciever is going to sleep, this happens when I don't use the remote for almost exactly 30 seconds. Then I have to press a button repeatedly and fast for it to get active again, then it responds to every key being pressed.

First I thought it had something to do with XBMC but it doesn't. It's the same when running irw, if I press the buttons slowly nothing is registered, but if I repeatedly press a button fast it start recognizing the keys being pressed and then I can press the buttons one by one slowly and every button get recognized. If I wait 30 seconds again it becomes inactive or what I should call it. I also tried different remotes with same result. And also on two different NUCs, both being D34010WYK.

Any ideas?

Thanks for reading

---

### Post by Jaman42 on 2014-08-18
As a note, the remotes works flawlessly on DN2820. Any ideas on how I could track down whats causing this?

---

### Post by Jaman42 on 2014-08-19
dmesg shows the following, is this a concern?

```
[   22.051127] Registered IR keymap rc-rc6-mce[   22.051252] input: Nuvoton w836x7hg Infrared Remote Transceiver as /devices/pnp0/00:08/rc/rc0/input4
[   22.051400] rc0: Nuvoton w836x7hg Infrared Remote Transceiver as /devices/pnp0/00:08/rc/rc0
[   22.061430] IR NEC protocol handler initialized
[   22.066783] IR RC5(x) protocol handler initialized
[   22.072502] mei_me 0000:00:16.0: irq 62 for MSI/MSI-X
[   22.074869] IR RC6 protocol handler initialized
[   22.079348] IR JVC protocol handler initialized
[   22.083777] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   22.083787] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.083793] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[   22.083798] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[   22.083803] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.083805] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[   22.083810] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[   22.083814] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   22.083816] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   22.089695] IR Sony protocol handler initialized
[   22.095076] IR SANYO protocol handler initialized
[   22.099127] nuvoton_cir: driver has been successfully loaded
[   22.106291] input: MCE IR Keyboard/Mouse (nuvoton-cir) as /devices/virtual/input/input5
[   22.106390] IR MCE Keyboard/mouse protocol handler initialized
[   22.106778] lirc_dev: IR Remote Control driver registered, major 248
[   22.111110] rc rc0: lirc_dev: driver ir-lirc-codec (nuvoton-cir) registered at minor = 0
[   22.111115] IR LIRC bridge handler initialized
```

---

### Post by Jaman42 on 2014-08-24
[COLOR=#000000][FONT=Verdana]Not sure what this mean but if I do cat /dev/lirc0 I get immediate response on the first button pressed. And as I said earlier with irw I need to repeatedly press a button for it to start recognizing keys being pressed.[/FONT][/COLOR]

---

### Post by Jaman42 on 2014-08-24
[COLOR=#000000][FONT=Verdana]I thought /dev/lirc0 was the same as in my case /dev/input/event4 since /dev/lirc0 was the only thing showing up when doing a dpkg-reconfigure lirc. However I got it set up using /dev/input/event4 and everything is working great![/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]This where the steps I did:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]* dpkg-reconfigure lirc (linux input layer)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]* In hardware.conf REMOTE_DEVICE="/dev/input/event4"[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]* irrecord -d /dev/input/event4 -H devinput /etc/lirc/lircd.conf[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Then it made a lircd.conf.conf which I renamed to lircd.conf (replacing the existing) and modified hardware.conf REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf".[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]And now everything is working![/FONT][/COLOR]

---

