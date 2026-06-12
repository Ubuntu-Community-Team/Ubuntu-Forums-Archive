---
title: "USB IRBlaster issues"
date: 2013-06-28
forum: Hardware
---

### Post by dusanmal on 2013-06-28
Hello,
I am creating a MythTVbox based on Uuntu 12.04. As a method for changing channels on the Verizon FIOS Mtorola qip7100 receiver I want to use USB IRBlaster. I followed general FAQ's and instructions for this but I am stumbling on what I think is  a hardware issue. LIRC is installed and running, conf files are there... Please check following relevant logs - any help in interpreting what is wrong and correcting it is more than welcome:

Command:  irsend SEND_ONCE Motorola_QIP6200-2 power
have been issued at the point in the log after FTDI device was recognized...

root@myth:/var/log# tail syslog
Jun 28 22:02:29 myth kernel: [391792.144648] usb 1-1.2: Endpoint 2 MaxPacketSize 64
Jun 28 22:02:29 myth kernel: [391792.144653] usb 1-1.2: Setting MaxPacketSize 64
Jun 28 22:02:29 myth kernel: [391792.145172] usb 1-1.2: FTDI USB Serial Device converter now attached to ttyUSB0
Jun 28 22:02:29 myth mtp-probe: bus: 1, device: 5 was not an MTP device
Jun 28 22:03:00 myth lircd-0.9.0[8699]: accepted new client on /var/run/lirc/lircd
Jun 28 22:03:00 myth lircd-0.9.0[8699]: Initializing FTDI: /dev/ttyUSB0
Jun 28 22:03:00 myth lircd-0.9.0[8699]: device configuration option must contain an '=': '/dev/ttyUSB0'
Jun 28 22:03:00 myth lircd-0.9.0[8699]: Failed to initialize hardware
Jun 28 22:03:00 myth lircd-0.9.0[8699]: hwftdi_send() carrier=38000Hz f_sample=524288Hz 
Jun 28 22:03:00 myth lircd-0.9.0[8699]: removed client

Any ideas? Please feel free to ask me for more detals, I m attempting to keep this post as brief as I can.

---

