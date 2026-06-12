---
title: "Cannot initialize Bluetooth 3Com PCMCIA (3CRWB6096)"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by aelfraithr on 2007-04-21
Hello all

I have a Dell Latitude C610 laptop with Ubuntu 7.04 (freshly upgraded)

I'm trying to use a 3Com Bluetooth PCMCIA card, model 3CRWB6096 version 2.0

I followed this guide in order to install necessary software, download the firmware, etc.

[http://www.dotmana.com/index.php/?p=265](http://www.dotmana.com/index.php/?p=265)

However when I try to initialize the card with 

[INDENT]sudo hciconfig hci0 up[/INDENT]

I get:

[INDENT]Can't init device hci0: Connection timed out (110)[/INDENT]

This is the relevant part of syslog after restarting the bluetooth daemon and inserting the PCMCIA card:

[INDENT]Apr 21 17:47:13 fourier hcid[5473]: Bluetooth HCI daemon
Apr 21 17:47:13 fourier hcid[5473]: Starting SDP server
Apr 21 17:47:32 fourier kernel: [ 1140.628000] pccard: PCMCIA card inserted into slot 0
Apr 21 17:47:32 fourier kernel: [ 1140.628000] pcmcia: registering new device pcmcia0.0
Apr 21 17:47:33 fourier hcid[5473]: HCI dev 0 registered
Apr 21 17:47:33 fourier hcid[5473]: Default passkey agent (:1.8, /org/bluez/applet) registered
Apr 21 17:47:34 fourier NetworkManager: <debug info>^I[1177170454.002275] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_104c_ac51_bluetooth_hci'). 
Apr 21 17:47:34 fourier NetworkManager: <debug info>^I[1177170454.050525] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Apr 21 17:47:43 fourier hcid[5498]: Can't init device hci0: Connection timed out (110)[/INDENT]

When I do a "hciconfig" I get this:

[INDENT]hci0:	Type: PCCARD
	BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
	DOWN 
	RX bytes:0 acl:0 sco:0 events:0 errors:0
	TX bytes:4 acl:0 sco:0 commands:1 errors:0[/INDENT]

Can anyone help me with this? Do I need a new BT card? or a new laptop? or a new brain? :) 

KInd regards

Alf

---

### Post by aelfraithr on 2007-04-21
HI, it's me again :)

With my other laptop, a Lenovo X60, and Ubuntu 6.10, it works fine.

So it's either the laptop hardware or the upgrade to 7.04.

Stay tuned...

Alf

---

### Post by ironblade on 2007-06-22
Hi,

I'm in the same boat - same card, same errors, different laptop (HP Compaq nc6000).
Any news on this?

Cheers!

---

### Post by ironblade on 2007-06-22
Ok, so I just rebooted (overnight - shut down and boot up) and when I logged into KDE, I got the happy message "Bluetooth Adaptor found".
In konqueror, I went to bluetooth:/ and it found nearby BT devices.
So the reboot magic worked for me.
BTW, I made sure I got the firmware from the drivers on the 3com website, not from my driver cd.

Good luck to you. :)

---

