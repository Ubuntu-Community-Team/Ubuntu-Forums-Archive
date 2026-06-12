---
title: "Dell XPS 13 9350 USB-C HDMI: no signal"
date: 2016-08-05
forum: Hardware
---

### Post by geddeth on 2016-08-05
I have just received a brand new Dell XPS 13. It came preinstalled with Windows, but I switched to AHCI mode and installed Ubuntu 16.04 on it. After some issues with the Broadcom wifi drivers, I could finally start using the machine for work.

Now I am attempting to attach an external monitor (Dell 24") to the USB-C TB3 connector, and having nothing but trouble. 

I started by purchasing a noname USB-C to HDMI adapter, this one:
[IMG]https://www.av-cables.dk/images.php/295x199/1435327430106480042ee.jpg[/IMG]

When entering the Displays manager in Ubuntu, I cannot see the monitor at all.
Hotplugging and rebooting with the monitor connected makes no difference.

I did a firmware upgrade to 1.4.4 with no effect.
I upgraded to latest mainline kernel 4.6.5 with no effect.
I have disabled Secure Boot and Thunderbolt user security in BIOS.
I have tried with a different external monitor. 

Nothing has so far made any difference at all. I see nothing in [FONT=Courier New]dmesg[/FONT] or [FONT=Courier New]lspci[/FONT] that seems to identify any action or change I make with this adapter and monitor. I have spent a few days on this problem now. Any ideas?

---

### Post by svast on 2016-08-07
hello

personnally, I have purchased the DELL DA200 , which provides Ethernet/USB3/VGA/HDMI connected to the TB3/USB-C port.
With Windows10, I could verify that all ports are doing the job, but within Ubuntu : HDMI does not work at all.
I have BIOS 1.4.4 as well, Ubuntu 16.04 along with 4.4.0-31 kernel

Never managed to get HDMI output.
By the way, I also purchased USB-C to DisplayPort from Google store: It does work, and event able to do MST daisy chaining.

Still I am interested in having a solution towards HDMI, my searches came to nothing good so far.

---

### Post by geddeth on 2016-08-08
@svast: thanks for your reply.

Can you link me the USB-C <> DisplayPort adapter that you mentioned?

---

### Post by svast on 2016-08-09
@geddeth: Sure, here it is:

[https://store.google.com/product/usb_type_c_to_displayport_cable](https://store.google.com/product/usb_type_c_to_displayport_cable)

---

### Post by chronos00 on 2017-07-17
I am having the exact same issue with external USB-C to HDMI adapter.

Ware any of you able to get these adapters working?

Thank you!

---

