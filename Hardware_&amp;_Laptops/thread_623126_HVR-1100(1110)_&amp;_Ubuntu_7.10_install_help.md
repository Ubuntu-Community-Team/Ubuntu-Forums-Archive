---
title: "HVR-1100(1110) &amp; Ubuntu 7.10 install help"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by Nedtlele on 2007-11-25
**Solved - see 2nd page.**


------------------------------------------------------------------------------
Hello,

I recently started making the transition over to Linux, I installed Ubuntu 7.10.

I have read up as much as possible, and have been trying for 3 days to get my HVR-1110 up and running.

Using the guide: (and all other stuff I could find with google)

[http://linuxtv.org/wiki/index.php/Ha...g_the_Firmware](http://linuxtv.org/wiki/index.php/Ha...g_the_Firmware)



Have been trying to follow it as close as seems possible.

But have reached a juncture that I need help with.
In the guide it mentions firmware dvb-fe-tda10046.fw
But I was unable to get it as all links were dead.

Today I managed to find a link for it, and downloaded it.

The guide shows it "place a copy of the firmware file in your /lib/firmware directory" which I have finally managed to do.

Then is shows I need to place this line:

"install saa7134 /sbin/modprobe --ignore-install saa7134 && { /sbin/modprobe saa7134-alsa; } && { /sbin/modprobe saa7134-dvb;}"

into the "/etc/modprobe.conf"
which Ubuntu I found out, does not have.

So I created the file using "touch modprobe.conf" command,
(if I recall correctly)
and now I have the file "modprobe.conf" which I added the line to.

Everything seems to be there now, but when I run Kaffeine or TVTime,
they do not find any channels..

It seems to me I have had to do things slightly differently to the guide(s) as some of the things I couldn't do, and getting firmware and copying it in manually. ( which was a task in it's self for me being so new to Linux)
But all the devices seems to be there, devices check out when I follow the tests at the guide. I am just hopefully one step away from the tv working.
(he says with fingers crossed)

I should say I did see a channel pop up(what looked like Analog tv) for a split second, when Tvtime was trying to tune. And Kaffiene just stops searching as it seems there is no signal, if I'm reading the thing right.
Also the card does work as I use it in windows.


After 3 days of this I am stumped as to what I can do now, with my little Linux knowledge.

Any help would be greatly appreciated.

Thanks.
Edit/Delete Message

Edit:
This is part of the dmesg that has some info, if it helps diagnose.

----
[   29.659549] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.714185] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.800524] input: PC Speaker as /class/input/input3
[   29.961368] Linux video capture interface: v2.00
[   30.036193] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   30.036203] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   30.036374] atl1 0000:02:00.0: version 2.0.7
[   30.078559] saa7130/34: v4l2 driver version 0.2.14 loaded
[   30.078606] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   30.078612] saa7133[0]: found at 0000:05:02.0, rev: 209, irq: 18, latency: 64, mmio: 0xfebff800
[   30.078617] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
[   30.078625] saa7133[0]: board init: gpio is 6400000
[   30.091265] usbcore: registered new interface driver lmpcm_usb
[   30.091268] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   30.206811] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   30.206988] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   30.221696] input: HVR 1110 as /class/input/input4
[   30.221719] ir-kbd-i2c: HVR 1110 detected at i2c-0/0-0071/ir0 [saa7133[0]]
[   30.289506] saa7133[0]: i2c eeprom 00: 70 00 01 67 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   30.289512] saa7133[0]: i2c eeprom 10: ff ff ff 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   30.289517] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 33 88 ff 00 aa ff ff ff ff
[   30.289521] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.289526] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 60 ff ff ff ff ff ff
[   30.289530] saa7133[0]: i2c eeprom 50: ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   30.289535] saa7133[0]: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   30.289539] saa7133[0]: i2c eeprom 70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   30.289543] saa7133[0]: i2c eeprom 80: 84 09 00 04 20 77 00 40 5b 62 0d f0 73 05 29 00
[   30.289548] saa7133[0]: i2c eeprom 90: 84 08 00 06 cb 05 01 00 94 38 89 72 07 70 73 09
[   30.289553] saa7133[0]: i2c eeprom a0: 23 5f 73 0a fc 72 72 0b 2f 72 0e 01 72 0f 03 72
[   30.289557] saa7133[0]: i2c eeprom b0: 10 01 72 11 ff 79 84 00 00 00 00 00 00 00 00 00
[   30.289562] saa7133[0]: i2c eeprom c0: 84 09 00 04 20 77 00 40 5b 62 0d f0 73 05 29 00
[   30.289566] saa7133[0]: i2c eeprom d0: 84 08 00 06 cb 05 01 00 94 38 89 72 07 70 73 09
[   30.289571] saa7133[0]: i2c eeprom e0: 23 5f 73 0a fc 72 72 0b 2f 72 0e 01 72 0f 03 72
[   30.289575] saa7133[0]: i2c eeprom f0: 10 01 72 11 ff 79 84 00 00 00 00 00 00 00 00 00
[   30.289583] tveeprom 0-0050: Hauppauge model 67019, rev B3B4, serial# 877147
[   30.289585] tveeprom 0-0050: MAC address is 00-0D-FE-0D-62-5B
[   30.289587] tveeprom 0-0050: tuner model is Philips 8275A (idx 114, type 4)
[   30.289589] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
[   30.289591] tveeprom 0-0050: audio processor is SAA7131 (idx 41)
[   30.289592] tveeprom 0-0050: decoder processor is SAA7131 (idx 35)
[   30.289593] tveeprom 0-0050: has radio, has IR receiver, has IR transmitter
[   30.289595] saa7133[0]: hauppauge eeprom: model=67019
[   30.425246] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   30.453189] tuner' 0-004b: chip found @ 0x96 (saa7133[0])
[   30.572957] tda8290 0-004b: setting tuner address to 61
[   30.752607] tda8290 0-004b: type set to tda8290+75a
 32.200702] saa7133[0]: registered device video0 [v4l2]
[   32.200732] saa7133[0]: registered device vbi0
[   32.200757] saa7133[0]: registered device radio0
[   32.297577] saa7134 ALSA driver for DMA sound loaded
[   32.297597] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 18 registered as card -2
[   32.361530] DVB: registering new adapter (saa7133[0])
[   32.361534] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   32.461316] tda1004x: setting up plls for 48MHz sampling clock
[   32.824593] tda1004x: found firmware revision 20 -- ok
[   33.124087] lp: driver loaded but no devices found


-------

Edit:
Edit:
Using 7.10 Ubuntu
Have TVtime and Kaffiene installed, they both fail to pick up any channels when scanning.
Card does work in windows ( only thing keeping windows on my HD at the mo )


Edit 2:
Just as I finished typing this, closed Firefox, and seen there was a picture in Tvtime ( must of left it scanning and forgot about it )
But it did make me laugh :)

The picture looks like it's analog, and there is no sound. So no Digital signal being recieved.


Glad I'm getting closer though.

Edit:
This is part of the dmesg that has some info , if it helps diagnose.
-----------
[ 29.659549] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 29.714185] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 29.800524] input: PC Speaker as /class/input/input3
[ 29.961368] Linux video capture interface: v2.00
[ 30.036193] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 30.036203] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 30.036374] atl1 0000:02:00.0: version 2.0.7
[ 30.078559] saa7130/34: v4l2 driver version 0.2.14 loaded
[ 30.078606] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[ 30.078612] saa7133[0]: found at 0000:05:02.0, rev: 209, irq: 18, latency: 64, mmio: 0xfebff800
[ 30.078617] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
[ 30.078625] saa7133[0]: board init: gpio is 6400000
[ 30.091265] usbcore: registered new interface driver lmpcm_usb
[ 30.091268] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[ 30.206811] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[ 30.206988] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 30.221696] input: HVR 1110 as /class/input/input4
[ 30.221719] ir-kbd-i2c: HVR 1110 detected at i2c-0/0-0071/ir0 [saa7133[0]]
[ 30.289506] saa7133[0]: i2c eeprom 00: 70 00 01 67 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[ 30.289512] saa7133[0]: i2c eeprom 10: ff ff ff 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[ 30.289517] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 33 88 ff 00 aa ff ff ff ff
[ 30.289521] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 30.289526] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 60 ff ff ff ff ff ff
[ 30.289530] saa7133[0]: i2c eeprom 50: ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 30.289535] saa7133[0]: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 30.289539] saa7133[0]: i2c eeprom 70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 30.289543] saa7133[0]: i2c eeprom 80: 84 09 00 04 20 77 00 40 5b 62 0d f0 73 05 29 00
[ 30.289548] saa7133[0]: i2c eeprom 90: 84 08 00 06 cb 05 01 00 94 38 89 72 07 70 73 09
[ 30.289553] saa7133[0]: i2c eeprom a0: 23 5f 73 0a fc 72 72 0b 2f 72 0e 01 72 0f 03 72
[ 30.289557] saa7133[0]: i2c eeprom b0: 10 01 72 11 ff 79 84 00 00 00 00 00 00 00 00 00
[ 30.289562] saa7133[0]: i2c eeprom c0: 84 09 00 04 20 77 00 40 5b 62 0d f0 73 05 29 00
[ 30.289566] saa7133[0]: i2c eeprom d0: 84 08 00 06 cb 05 01 00 94 38 89 72 07 70 73 09
[ 30.289571] saa7133[0]: i2c eeprom e0: 23 5f 73 0a fc 72 72 0b 2f 72 0e 01 72 0f 03 72
[ 30.289575] saa7133[0]: i2c eeprom f0: 10 01 72 11 ff 79 84 00 00 00 00 00 00 00 00 00
[ 30.289583] tveeprom 0-0050: Hauppauge model 67019, rev B3B4, serial# 877147
[ 30.289585] tveeprom 0-0050: MAC address is 00-0D-FE-0D-62-5B
[ 30.289587] tveeprom 0-0050: tuner model is Philips 8275A (idx 114, type 4)
[ 30.289589] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
[ 30.289591] tveeprom 0-0050: audio processor is SAA7131 (idx 41)
[ 30.289592] tveeprom 0-0050: decoder processor is SAA7131 (idx 35)
[ 30.289593] tveeprom 0-0050: has radio, has IR receiver, has IR transmitter
[ 30.289595] saa7133[0]: hauppauge eeprom: model=67019
[ 30.425246] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[ 30.453189] tuner' 0-004b: chip found @ 0x96 (saa7133[0])
[ 30.572957] tda8290 0-004b: setting tuner address to 61
[ 30.752607] tda8290 0-004b: type set to tda8290+75a
32.200702] saa7133[0]: registered device video0 [v4l2]
[ 32.200732] saa7133[0]: registered device vbi0
[ 32.200757] saa7133[0]: registered device radio0
[ 32.297577] saa7134 ALSA driver for DMA sound loaded
[ 32.297597] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 18 registered as card -2
[ 32.361530] DVB: registering new adapter (saa7133[0])
[ 32.361534] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[ 32.461316] tda1004x: setting up plls for 48MHz sampling clock
[ 32.824593] tda1004x: found firmware revision 20 -- ok
[ 33.124087] lp: driver loaded but no devices found
------

Edit:
I think this is the bit of the guide that has caused a problem, bing that Ubuntu has no modprobe.conf.

Quote:
Making the Modules Load into the Kernel at Startup

In order that the saa7134-svb module gets loaded at startup add following line

install saa7134 /sbin/modprobe --ignore-install saa7134 && { /sbin/modprobe saa7134-alsa; } && { /sbin/modprobe saa7134-dvb;}

to the modprobe.conf in

/etc/modprobe.conf

thanks :-)

---

### Post by Nedtlele on 2007-11-25
Can anyone point me in the right direction? Every guide I have read is out of date.

Edit :
 Ok, I figure out after some help from Scooby, that I need to add the line to modprobe.d

Now can anyone tell me how I go about adding a line of text into what I see as a folder.  What commands i use ?

I tried using "By the power of Grey Skull!!" but it had no effect.

---

### Post by Nedtlele on 2007-11-25
Ok,  i see maybe I have to go to /etc/modprobe.b and use "options" infront of the line i need, reading it:

"options install saa7134 /sbin/modprobe --ignore-install saa7134 && { /sbin/modprobe saa7134-alsa; } && { /sbin/modprobe saa7134-dvb;}"

....maybe?

Ok got the line added to the file "options" in etc/modprobe.d

restarted,  I have a couple of analog channels, but no digital.
and no sound.

stumped again.

feel free to help out :-)

---

### Post by Nedtlele on 2007-11-25
ok, following this guide here [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php)
started the scan to see if there was tv and got this :


~$ sudo -s -H
root@Perk:/home/j3# mkdir /root/.tzap
root@Perk:/home/j3# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 754166670 0 3 9 1 0 0 0
>>> tune to: 754166670:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 754166670:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

Edit:

Also tested the status of the card  :

j3@Perk:~$ grep -i dvb /var/log/messages
Nov 25 00:59:18 Perk kernel: [   30.970239] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 00:59:18 Perk kernel: [   34.818403] DVB: registering new adapter (saa7133[0]).
Nov 25 00:59:18 Perk kernel: [   34.818407] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 01:31:12 Perk kernel: [   30.184240] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 01:31:12 Perk kernel: [   34.091559] DVB: registering new adapter (saa7133[0]).
Nov 25 01:31:12 Perk kernel: [   34.091563] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 04:13:33 Perk kernel: [   26.427898] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 04:13:33 Perk kernel: [   30.489384] DVB: registering new adapter (saa7133[0]).
Nov 25 04:13:33 Perk kernel: [   30.489389] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 05:25:56 Perk kernel: [   32.075677] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 05:25:56 Perk kernel: [   32.283781] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
Nov 25 05:25:56 Perk kernel: [   34.338493] DVB: registering new adapter (saa7133[0])
Nov 25 05:25:56 Perk kernel: [   34.338497] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 06:03:59 Perk kernel: [   32.204903] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 06:03:59 Perk kernel: [   32.416131] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
Nov 25 06:03:59 Perk kernel: [   34.458867] DVB: registering new adapter (saa7133[0])
Nov 25 06:03:59 Perk kernel: [   34.458871] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 13:44:08 Perk kernel: [   31.819067] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 13:44:08 Perk kernel: [   32.029397] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
Nov 25 13:44:08 Perk kernel: [   34.116026] DVB: registering new adapter (saa7133[0])
Nov 25 13:44:08 Perk kernel: [   34.116030] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 16:15:59 Perk kernel: [   32.374665] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 16:15:59 Perk kernel: [   32.586008] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
Nov 25 16:15:59 Perk kernel: [   34.660637] DVB: registering new adapter (saa7133[0])
Nov 25 16:15:59 Perk kernel: [   34.660640] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 20:10:56 Perk kernel: [   24.355148] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 20:10:56 Perk kernel: [   24.565350] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
Nov 25 20:10:56 Perk kernel: [   26.632015] DVB: registering new adapter (saa7133[0])
Nov 25 20:10:56 Perk kernel: [   26.632019] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 20:38:00 Perk kernel: [   30.078617] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 20:38:00 Perk kernel: [   30.289589] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
Nov 25 20:38:00 Perk kernel: [   32.361530] DVB: registering new adapter (saa7133[0])
Nov 25 20:38:00 Perk kernel: [   32.361534] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 22:24:42 Perk kernel: [   30.875045] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 22:24:42 Perk kernel: [   31.083692] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
Nov 25 22:24:42 Perk kernel: [   33.139664] DVB: registering new adapter (saa7133[0])
Nov 25 22:24:42 Perk kernel: [   33.139668] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 22:41:37 Perk kernel: [   35.933158] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 22:41:37 Perk kernel: [   36.142230] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
Nov 25 22:41:37 Perk kernel: [   38.186239] DVB: registering new adapter (saa7133[0])
Nov 25 22:41:37 Perk kernel: [   38.186243] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
Nov 25 23:46:32 Perk kernel: [   31.484420] saa7133[0]: subsystem: 0070:6701, board: Hauppauge WinTV-HVR1110 DVB-T/Hybrid [card=104,autodetected]
Nov 25 23:46:32 Perk kernel: [   31.695926] tveeprom 0-0050: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
Nov 25 23:46:32 Perk kernel: [   33.755908] DVB: registering new adapter (saa7133[0])
Nov 25 23:46:32 Perk kernel: [   33.755913] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...

If there's anything I can post to help find a solution just say.
THanks

---

### Post by Nedtlele on 2007-11-25
Should I just reinstall Ubuntu and start again?  Should it just work with this newr 7.10 Ubuntu?

I've exausted all guides and out of ideas now.

---

### Post by jcsteele on 2007-11-25
Have you taken a look at [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

There is alot of information (and links to information) on setting TV Tuner cards.

//jcs

---

### Post by Nedtlele on 2007-11-25
Yep. a few hundred lines of text above your post  is that exact link  :)

Edit:
 Ok now I have 4 channels digital with sound..somthings up though as they are BBC1 BBC2 BBC3 & BBC news24

Obviously with all the different things from different guides I have done have kind of got it working but also wedged up the channel search.
WHen I go into Kaffiene and set any location and search, I get those 4 channels every time.

:lolflag:

I notice my channles.conf is empty, so it has not channels in there, I wonder where they're being stalled.
Seems I've got a proper messed up install now.

---

### Post by jcsteele on 2007-11-26
Sorry must of missed that.

Do you remember the steps you took to get it semi-working?  Since your system is getting kinda cruddy, you can always reinstall if you can remember just WHAT steps you took that produced the best results...this sometimes works for me when tackling a hardware problem...you try so many things and they pile on top of each other until eventually things will NEVER work.....then its time for a reinstall.

Sorry I could not help you more.

//jcs

---

### Post by Nedtlele on 2007-11-26
No problem, thanks for trying, yes i think I'll reinstall, but unfortunetly the only guide that seemed to get anything working , was for Nova TV card, at MythTV.

I think once I have a good idea of how to get this card running I will write a simple 'how to' guide as the others seem t be out of date in one way or another.

Thanks again.

---

### Post by Nedtlele on 2007-11-26
Just reinstalled Ubunto 7.10

Does anyone have a link to a guide or guide that they have used and know works with 7.10 please.

Or if someone who has this card could put the process they went through to get it running.

Thanks

---

### Post by Nedtlele on 2007-11-26
Ok, trying again, this time I followed this guide:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110)


Eveything has checked out ok up to this point, and this is where I could do with some help, about the kernel ;


Quote:
------------------
 Installing the Firmware

This card requires a firmware file (dvb-fe-tda10046.fw) for the demodulator, which can be obtained using the get_dvb_firmware perl script included in the kernel sources:

[B]# cd /[kernel source directory]/Documentation/dvb/
# perl get_dvb_firmware tda10046[/B]

Once the download is complete, place a copy of the firmware file in your /lib/firmware directory. (This directory may differ with some distros; consult your distro's documentation for the appropriate location).
Making the Modules Load into the Kernel at Startup

In order that the saa7134-svb module gets loaded at startup add following line

install saa7134 /sbin/modprobe  --ignore-install saa7134 && { /sbin/modprobe saa7134-alsa; } && { /sbin/modprobe saa7134-dvb;}

to the modprobe.conf in

/etc/modprobe.conf

Now check whether everything is working as it should. Restart the PC and check the /var/log/messages. Look out for something like:

kernel: DVB: registering new adapter (saa7133[0]).
kernel: DVB: registering frontend 1 (Philips TDA10046H DVB-T)...

telling you the dvb modules got loaded. Please note that in this case the system has two DVB cards. The second one (frontend 1) is the HVR 1110.

kernel: tda1004x: found firmware revision 20 -- ok

tells you that firmware has also been loaded. 
---------------------
END Quote.

The part I put in Bold, is the part I am stuck at,

and also the modprobe.conf part,  is where I think I have to gedit the "options" file in "modprobe.d" as there is no modprobe.conf in Ubu 7.10 ( yes?)


Thanks.

---

### Post by Nedtlele on 2007-11-26
Woot!

All running in Kaffeine .
I will try to list how I got it running in the exact order.

This is for Ubuntu 7.10  64bit  + Hauppauge HVR-1100 (1110) for DVB

Started by using this guide.
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110)

You can skip straight to the part:
**Quote--**
* Installing the Firmware*

This card requires a firmware file (dvb-fe-tda10046.fw) for the demodulator, which can be obtained using the get_dvb_firmware perl script included in the kernel sources:

# cd /[kernel source directory]/Documentation/dvb/
# perl get_dvb_firmware tda10046

Once the download is complete, place a copy of the firmware file in your /lib/firmware directory. (This directory may differ with some distros; consult your distro's documentation for the appropriate location). 

**END quote--**


To do the above I 
**Downloaded the firmware script by itself**: 

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=Documentation/dvb/get_dvb_firmware;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=Documentation/dvb/get_dvb_firmware;hb=HEAD)

**And then Save Page As**

 "get_dvb_firmware"  - without quotes


**Change directory (cd) to the folder where you saved it**


**Now in terminal use**

perl get_dvb_firmware tda10046

[B]
Copy the resulting file ( dvb-fe-tda10046.fw ) to /lib/firmware[/B]

sudo cp dvb-fe-tda10046.fw /lib/firmware


**You can skip the part**

"Making the Modules Load into the Kernel at Startup"

And move onto the initial scan.

[http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device](http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device)

**First get the scan utility described here:**

[http://www.linuxtv.org/wiki/index.php/LinuxTV_dvb-apps](http://www.linuxtv.org/wiki/index.php/LinuxTV_dvb-apps)

**Using this **

sudo apt-get install dvb-utils

[B]
Then change directory to the utils folder[/B]

 cd /usr/share/doc/dvb-utils

 mkdir -p ~/.tzap


**Inside the Scan folder there are files relating to the frequency required for the initial scan**
**Located here**

usr/share/doc/dvb-utils/examples/scan

**My transmitter is in the UK, and  nearest one Crystal Palace,  so I used the name of the corresponding file in the Scan command**.
**Just use whichever one you need for your country, swapping ou**t "uk-CrystalPalace"

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace > ~/.tzap/channels.conf



That was it, ran Kaffeine and scanned for channels, and they were all there!
Which was nice!

Hope this helps someone else, if not, I'm sure it will help me again, when I have to reinstall.

Thanks to "sn9" on  IRC  #linuxtv who made it so simple!
:guitar:

---

### Post by hecatae on 2008-05-12
thank you for all the hard work, I had an issue with sound previously after spending time getting the dvb working.

going to have another crack this week.

---

### Post by megamania on 2008-05-19
> **Nedtlele said:**
> 
sudo apt-get install dvb-utils

Then change directory to the utils folder[/B]

 cd /usr/share/doc/dvb-utils

 mkdir -p ~/.tzap


**Inside the Scan folder there are files relating to the frequency required for the initial scan**
**Located here**

usr/share/doc/dvb-utils/examples/scan

**My transmitter is in the UK, and  nearest one Crystal Palace,  so I used the name of the corresponding file in the Scan command**.
**Just use whichever one you need for your country, swapping ou**t "uk-CrystalPalace"

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace > ~/.tzap/channels.conf

That was it, ran Kaffeine and scanned for channels, and they were all there!

Thanks so much for the info. It helped me a lot getting the dvb-t part of the card up-and-running.

There's something I'm missing however, and that's the connection between tzap and kaffeine.
What I understand is that if I scan the channels with Kaffeine, it does the same as the "scan" program, but using the frequency files in the Kaffeine directory.

I'm sure there's something I'm missing. Can anybody shed some light please?

---

