---
title: "So, what _is_ the current (2009/03/01) bluetooth status in Intrepid?"
date: 2009-03-01
forum: Hardware
---

### Post by dlacoste on 2009-03-01
OK, I've read about 4823190128349123 different articles in the last hour, with little success.

Here's what I know (and some explanation) :

In 8.04, I could get audio from Rhythmbox and absolutely nothing else, so I decided to upgrade to 8.10 because of the new and improved audio.

Yay!  On first config, everything worked: I had to do some manual moving things around (it defaulted to using onboard instead of my bluetooth headset) but then everything worked and It Was Good (TM).

Then I finally connected to the net and did an upgrade, and got a LOT of packages, including kernel 2.6.27-12

Well, now bluetooth doesn't work.

I did a remove and reinstall and reboot (after trying dozens of things) and I can show this:

Procedure:
1 - boot (no bluetooth present)
2 - login (no bluetooth present)
3 - insert bluetooth dongle (success: device appears)
4 - power on bluetooth headset (failure: kernel reports bluetoothd crashing in audio.so)

I can see dozens and dozens of people complaining about similar errors, and in the end this isn't "can you make audio work" or "can you make file transfers work" : it isn't getting that far.  The minute the device connects, bluetoothd crashes.

Any suggestions?

Thanks!

Mar  1 13:49:06 chili kernel: [  348.340013] usb 4-2: new full speed USB device using uhci_hcd and address 3
Mar  1 13:49:07 chili kernel: [  348.511168] usb 4-2: configuration #1 chosen from 1 choice
Mar  1 13:49:07 chili kernel: [  348.562460] Bluetooth: Generic Bluetooth USB driver ver 0.3
Mar  1 13:49:07 chili bluetoothd[8515]: HCI dev 0 registered
Mar  1 13:49:07 chili kernel: [  348.563324] usbcore: registered new interface driver btusb
Mar  1 13:49:07 chili bluetoothd[8515]: HCI dev 0 up
Mar  1 13:49:07 chili bluetoothd[8515]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/hci0
Mar  1 13:49:07 chili bluetoothd[8515]: Registered interface org.bluez.NetworkPeer on path /org/bluez/hci0
Mar  1 13:49:07 chili bluetoothd[8515]: Registered interface org.bluez.NetworkHub on path /org/bluez/hci0
Mar  1 13:49:07 chili bluetoothd[8515]: Registered interface org.bluez.NetworkRouter on path /org/bluez/hci0
Mar  1 13:49:07 chili bluetoothd[8515]: Registered interface org.bluez.Service on path /org/bluez/hci0
Mar  1 13:49:07 chili bluetoothd[8515]: Registered interface org.bluez.AudioSink on path /org/bluez/hci0/dev_00_1A_80_77_E6_60
Mar  1 13:49:07 chili bluetoothd[8515]: Registered interface org.bluez.Control on path /org/bluez/hci0/dev_00_1A_80_77_E6_60
Mar  1 13:49:07 chili bluetoothd[8515]: Adapter /org/bluez/hci0 has been enabled
Mar  1 13:49:07 chili bluetoothd[8515]: Starting security manager 0

Mar  1 13:49:27 chili bluetoothd[8515]: link_key_request (sba=00:19:86:00:01:F1, dba=00:1A:80:77:E6:60)
Mar  1 13:49:28 chili bluetoothd[8515]: link_key_request (sba=00:19:86:00:01:F1, dba=00:1A:80:77:E6:60)

Mar  1 13:49:28 chili kernel: [  370.379569] bluetoothd[8515]: segfault at 450 ip 00007ff7d284568b sp 00007fffdc798f40 error 4 in audio.so[7ff7d2837000+23000]

---

### Post by dlacoste on 2009-03-02
I tried reverting to an earlier kernel, and then gave up.

This morning, I thought I'd go through it again: maybe I could get some kind of dump working, and followed this procedure (all on latest (-12) kernel)

0 - add intel-hda to the blacklist in /etc/modprobe.d (I don't use my onboard audio) : I hope this had nothing to do with the result!
1 - Remove EVERYTHING to do with bluez via synaptic.  Notably, this did not include libbluetooth, as that is a dependency of, well, EVERYTHING.  that seems kinda dumb to me :(
2 - reboot, then add everything back in (specifically including bluez-sco and bluez-compat)
3 - add my bluetooth adapter back in (it's usb) and remove everything from my supported devices list via the bluetooth plugin.
4 - turn on my headphones (while tail -f on /var/log/syslog was running, so I could see the expected crash)

it didn't crash!  it didn't connect, either, but that's ok

5 - turn headphones off and then on, into pairing mode, and use the bluetooth plugin to "add a new device".

For some reason, I had to do this three times.  First time it got to the "pairing" part where it said "sending 0000" and it just sat there, nothing happened.  So I tried it again and it remembered, so it didn't even try (it remembered that it failed)

So I tried it again and it paired successfully this time, and added it ok.  No idea what the difference was, but it added it, no crashing, no failing.

6 - add info to ~/.asoundrc so that I can add the device into pulse ([http://fosswire.com/post/2008/10/better-bluetooth-audio/](http://fosswire.com/post/2008/10/better-bluetooth-audio/) for more info)

7 - Added device to pulsaudio (pactl load-module module-alsa-sink device="bluetooth")

ta-da!  it's all working, flash is working, rhythmbox is working...

The only scary part is that I have NO idea what I did: as far as I can tell it's exactly the same, it's just working now.

Maybe someone in the future will do a search and this will help them :)

---

