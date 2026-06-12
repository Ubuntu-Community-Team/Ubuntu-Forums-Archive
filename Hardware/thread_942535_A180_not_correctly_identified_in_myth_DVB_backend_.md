---
title: "A180 not correctly identified in myth DVB backend setup, no channel lock"
date: 2008-10-09
forum: Hardware
---

### Post by biggyfred on 2008-10-09
Hello everyone,

I've been wrestling with the Avermedia A180 for a couple of days now. I've just loaded up Mythbuntu 8.04, but it keeps showing the card as an Air2PC v2 in the DVB section of the capture card mythtv backend setup. This morning, I formatted and reloaded Mythbuntu to start from scratch and used the tut by Cresho in post #4 (word for word) of this thread ([http://ubuntuforums.org/showthread.php?t=715165](http://ubuntuforums.org/showthread.php?t=715165)) as my guide. Using the Air2PC setup, I get no channel locks. I set this card up in mythtv a fair while back and it worked fine, and remember it showing up as nextwave or something of that nature in the mythtv setup. I can't seem to find an answer. Any help would be really appreciated.

Relevant parts of my:

dmesg:
```

[  215.694073] saa7133[0]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,autodetected]
[  215.694081] saa7133[0]: board init: gpio is 310480
[  215.829578] saa7133[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[  215.829586] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[  215.829591] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00
[  215.829596] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[  215.829601] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[  215.829606] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  215.829611] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  215.829617] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[  215.839301] saa7133[0]: registered device video0 [v4l2]
[  215.839323] saa7133[0]: registered device vbi0
[  215.874776] saa7134 ALSA driver for DMA sound loaded
[  215.874801] saa7133[0]/alsa: saa7133[0] at 0xfdbfe000 irq 22 registered as card -2
[  215.925485] nxt200x: NXT2004 Detected
[  215.953648] DVB: registering new adapter (saa7133[0])
[  215.953653] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[  215.961456] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[  215.973630] nxt2004: Waiting for firmware upload(2)...
[  217.515838] nxt2004: Firmware upload complete
```

lspci -vnn:
```

03:08.0 Multimedia controller [0480]: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
	Subsystem: Avermedia Technologies Inc AVerTVHD MCE A180 [1461:1044]
	Flags: bus master, medium devsel, latency 84, IRQ 22
	Memory at fdbfe000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

```

ls -l /dev/dvb/adapter0:
```

crw-rw----+ 1 root video 212, 4 2008-10-09 09:07 demux0
crw-rw----+ 1 root video 212, 5 2008-10-09 09:07 dvr0
crw-rw----+ 1 root video 212, 3 2008-10-09 09:07 frontend0
crw-rw----+ 1 root video 212, 7 2008-10-09 09:07 net0

```

I have saa7134 on the blacklist and added saa7134-dvb to the blacklist. This is my lsmod after boot:

```

nxt200x                14596  1 
saa7134_dvb            16652  0 
saa7134_alsa           15424  0 
saa7134               131920  2 saa7134_dvb,saa7134_alsa

```

Again, any help would be appreciated. I'm at wit's end here. Thanks in advance. If I've left out relevant information, please let me know.

---

### Post by newlinux on 2008-10-09
Mine show up as an air2pc v2 when I set mine up in 8.04 for the frontend ID, so that is okay. All of your outputs look in place. I assume you only blacklisted saa7134 not saa7134-dvb? You need saa7134-dvb, from your lsmod that is in place. I actually did not need to blacklist saa7134 either.

The additional information I need is all of your myth card setup and scan settings, what type of signal you are trying tune (OTA ATSC or QAM)? 

Aside from that, the next thing to do would be to test the card outside of myth using dvb-utils.
```

sudo apt-get install dvb-utils
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.mplayer/channels.conf

```
(or use the QAM scan file if you are using QAM)

then you can look in your channels.conf file for channel names (what is before the first colon) and do:
```

mplayer dvb://channel

```
If nothing shows up in your channels.conf file it we'll troubleshoot that...

---

### Post by newlinux on 2008-10-09
you'd probably get more help if you put this in the mythbuntu or multimedia and video portion of the forums.

---

### Post by biggyfred on 2008-10-09
I've opened a new thread here: [http://ubuntuforums.org/showthread.php?p=5937249#post5937249](http://ubuntuforums.org/showthread.php?p=5937249#post5937249)

Thanks a ton dude. You're a stud in my book.

---

