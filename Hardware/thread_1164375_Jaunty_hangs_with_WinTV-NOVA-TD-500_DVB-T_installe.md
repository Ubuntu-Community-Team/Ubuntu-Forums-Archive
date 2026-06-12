---
title: "Jaunty hangs with WinTV-NOVA-TD-500 DVB-T installed"
date: 2009-05-19
forum: Hardware
---

### Post by geoff07 on 2009-05-19
I'm trying to build a MythTV box and tripping up at every stage. The current problem is that Jaunty hangs randomly when the DVB card is installed.  The hangs can occur in MythTV but also when say Firefox is run and Mythtv is not running.  So it seems to be system related rather than app-related.

The card is found correctly and set up by the system (see listing) so it does not seem to be a hardware issue

May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   19.862790] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   19.862812] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   21.810647] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   22.525265] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   22.525692] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   22.527592] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   22.762100] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   22.946020] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   22.947736] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   23.106042] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   23.285965] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
May 19 10:01:09 ubuntu-mythtv-pvr kernel: [   23.286320] usbcore: registered new interface driver dvb_usb_dib0700


In addition, I have done a complete memory test with no errors.

The hardware is a mini-itx VIA EPIA-SP eden motherboard, which I know is underpowered but still should not hang.  It has 512 MB and is in a Cubid 2799 case using the offset riser that comes with the case, using the lower slot.

Removing the Hauppauge card removes the problem and the system stays up indefinitely.  Also, putting the card into a beefy ATX machine did not seem to have the same problem.

My feeling is that is is a Jaunty/VIA problem but have no idea where to go next!  Diagnostic help welcome.

---

### Post by Kubunteando on 2009-07-30
I have the same card in an Intel chipset and it works fine.

Can you try the Karmic live CD?

I suspect it can be an issue with the motherboard chipset and probably it works better with a newer kernel.

Which is the exact model of your motherboard?
Usually VIA ITX motherboards have a combination of a few letters and numbers as the model.

---

