---
title: "Belkin F8T001 BT dongle support"
date: 2009-08-19
forum: Hardware
---

### Post by Infoteksec on 2009-08-19
Hi. I've looked through various forums and this issue crops up periodically and still seems not to be resolved.

I have a Belkin Bluetooth F8T001 dongle which is not getting loaded up correctly. I looked in DMESG and found ...

[ 8551.840111] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 8551.990326] usb 2-1: configuration #1 chosen from 1 choice
[ 8552.084215] Bluetooth: Broadcom Blutonium firmware driver ver 1.2
[ 8552.084265] usb 2-1: firmware: requesting BCM2033-MD.hex
[ 8552.100425] bcm203x_probe: Mini driver request failed
[ 8552.100451] bcm203x: probe of 2-1:1.0 failed with error -5
[ 8552.100533] usbcore: registered new interface driver bcm203x
[ 8552.132535] Bluetooth: Generic Bluetooth USB driver ver 0.3
[ 8552.132659] usbcore: registered new interface driver btusb
[ 8586.973287] wlan0: deauthenticated
[ 8587.972122] wlan0: direct probe to AP 00:14:bf:6c:66:74 try 1
[ 8587.973650] wlan0 direct probe responded
[ 8587.973664] wlan0: authenticate with AP 00:14:bf:6c:66:74
[ 8587.977811] wlan0: authenticated
[ 8587.977834] wlan0: associate with AP 00:14:bf:6c:66:74
[ 8587.982712] wlan0: RX ReassocResp from 00:14:bf:6c:66:74 (capab=0x1 status=0 aid=1)
[ 8587.982725] wlan0: associated
[ 9737.392164] usb 2-1: USB disconnect, address 2
[ 9743.136113] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 9743.342434] usb 3-1: configuration #1 chosen from 1 choice
[ 9743.345536] usb 3-1: firmware: requesting BCM2033-MD.hex
[ 9743.387605] bcm203x_probe: Mini driver request failed
[ 9743.387658] bcm203x: probe of 3-1:1.0 failed with error -5
peter@Huey:~$ 

Others have said everything was resolved having loaded Bluetooth support via the package manager - I looked at the list of what was already installed and found 4.32-0ubuntu4.1 was in place.

I'm using ubuntu 9.04 fully patched on an Acer Aspire One.

Any suggestions?

Solution:

It transpires that the dongle requests two firmware files but the ones on the distribution have the wrong name. The solution is to rename the files in /etc/firmware to exactly match what the dongle is expecting.

Peter

---

### Post by Infoteksec on 2009-08-19
Hmmm ... a bit of research led me to what might be the problem.  The DMESG entry indicated the driver is trying to find BCM2033-MD.hex but the /lib/firmware directory contains files with the filetype of .BIN c.f.:

peter@Huey:/lib/firmware$ ls BCM*
BCM2033-FW.BIN  BCM2033-MD.BIN

Should I simply rename the files? Are HEX and BIN one and the same??

Peter

---

### Post by Infoteksec on 2009-08-19
OK, I renamed the files, plugged in my dongle and DMESG no longer gives an error message so I guess either the driver is looking for the wrong files or the files have the wrong name.

Could someone with access to a maintainer have the problem fixed? I don't have the resources to check but I guess the problem is generic across the Linux community.

Next ... how do I know if the damn thing is working? I was sort of hoping that the network LED would change from off to, perhaps, green. Sigh!

Peter

---

### Post by clon on 2010-12-11
I had the same problem with my Belkin bluetooth usb F8T001 adapter.
The package for getting the .hex and .bin files is located at: 

[http://bluez.sourceforge.net/download/bluez-firmware-1.2.tar.gz](http://bluez.sourceforge.net/download/bluez-firmware-1.2.tar.gz)

Now I don't get the error message, but still I have some problem with bluetooth service. I keep trying to start it with
 
          [LIST]
[*]sudo service bluetooth start
[/LIST]

but when I ask for the service status with

            [LIST]
[*]sudo service bluetooth status
[/LIST]

I always get the same response: "bluetooth is not running"

Any suggestions?

---

