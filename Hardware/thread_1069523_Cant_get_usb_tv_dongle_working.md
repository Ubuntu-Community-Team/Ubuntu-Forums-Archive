---
title: "Cant get usb tv dongle working"
date: 2009-02-14
forum: Hardware
---

### Post by jamin_melville on 2009-02-14
Hi I'm trying to get a leadtek usb dtv dongle gold to work in the ubunt.

dmesg outputs:

 5851.176089] usb 2-5: new high speed USB device using ehci_hcd and address 3                                                                                   
[ 5851.314850] usb 2-5: configuration #1 chosen from 1 choice                                                                                                    
[ 5851.663803] usbcore: registered new interface driver hiddev                                                                                                   
[ 5851.671020] input: Leadtek WinFast DTV Dongle Gold as /devices/pci0000:00/0000:00:0b.1/usb2/2-5/2-5:1.1/input/input9                                          
[ 5851.733523] input,hidraw0: USB HID v1.01 Keyboard [Leadtek WinFast DTV Dongle Gold] on usb-0000:00:0b.1-5
[ 5851.746993] dvb-usb: found a 'Leadtek WinFast DTV Dongle Gold' in cold state, will try to load a firmware
[ 5851.747011] firmware: requesting dvb-usb-af9015.fw
[ 5851.828136] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[ 5851.918648] dvb-usb: found a 'Leadtek WinFast DTV Dongle Gold' in warm state.
[ 5851.918814] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 5851.919751] DVB: registering new adapter (Leadtek WinFast DTV Dongle Gold)
[ 5852.439710] af9013: firmware version:4.95.0
[ 5852.446991] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[ 5852.567852] tda18271 5-00c0: creating new instance
[ 5852.574862] TDA18271HD/C1 detected @ 5-00c0
[ 5852.868070] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:0b.1/usb2/2-5/input/input10
[ 5852.909189] dvb-usb: schedule remote query interval to 150 msecs.
[ 5852.909199] dvb-usb: Leadtek WinFast DTV Dongle Gold successfully initialized and connected.
[ 5853.091137] usbcore: registered new interface driver usbhid
[ 5853.092257] usbhid: v2.6:USB HID core driver
[ 5853.094098] usbcore: registered new interface driver dvb_usb_af9015
[ 6719.420189] ACPI: EC: GPE storm detected, transactions will use polling mode
[ 6719.920054] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 6927.460669] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
ben@ben-laptop:/lib/firmware$

so I think I've installed it alright? but there is no /dev/video0 which is what all the programs point to for using the tv tuner.

I'm not really sure what I'm doing so any help would be appreciated. thanks

---

### Post by makkus on 2009-03-28
Hi.

I got it working using these instructions:

[http://www.mythtv.org/wiki/Leadtek_Winfast_DTV_Dongle_Gold](http://www.mythtv.org/wiki/Leadtek_Winfast_DTV_Dongle_Gold)

The only thing that I can't get to work is the remote control. 10 or so keys (Keys 0-9, Arrows,...) are recognized via /dev/input/eventXX (strangely, it creates 2 of those), but the rest I can't seem to get working.

Anybody an idea?

Cheers.

---

### Post by The Browncoat Cat on 2011-02-09
> **makkus said:**
> Hi.

I got it working using these instructions:

[http://www.mythtv.org/wiki/Leadtek_Winfast_DTV_Dongle_Gold](http://www.mythtv.org/wiki/Leadtek_Winfast_DTV_Dongle_Gold)

This page has been deleted from the MythTV Wiki.  Any idea where another copy might be?

---

