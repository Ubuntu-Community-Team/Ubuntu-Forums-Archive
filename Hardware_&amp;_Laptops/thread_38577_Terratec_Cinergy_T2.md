---
title: "Terratec Cinergy T2"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by tvoss on 2005-06-01
Hi all,

as my TV died last week, I decided to replace it with a DVB-T receiver connected to my Aspire 1363 WLMi. I googled a few hours and finally reached [http://www.linuxtv.org](http://www.linuxtv.org). Thumbs up for this site, all relevant information especially an overview of currently supported hardware, applications and some recent HOW-TOs. 
I finally bought a Terratec Cinergy T2 USB Box (89 Euro) that works out of the box with Ubuntu Hoary and later. The box even has a small Tux on it, covered by the slogan "Yes, it supports Linux." :-) Just connect the box to the USB (has to be 2.0) port , attach the included antenna, scan for your locally available channels and fire up xine, mplayer, vdr etc :-) That's all. The box is powered by the host system it is connected to.

It was even harder to get the box to work under windows :-)))

I've switched to Breezy a few days ago, and it doesn't include vdr yet (in fact it does, but the package is broken because of the gcc 4.0 transition). Anyone out there who is using the box in conjunction with vdr? 

Just wanted to recommend a DVB-T receiver that just works.

Greetings Thomas


P.S.: To get the scan-utility: "apt-get install dvb-utils"

---

### Post by Pink Chick on 2005-06-27
[QUOTE=tvoss]Hi all,

as my TV died last week, I decided to replace it with a DVB-T receiver connected to my Aspire 1363 WLMi. I googled a few hours and finally reached [http://www.linuxtv.org](http://www.linuxtv.org). Thumbs up for this site, all relevant information especially an overview of currently supported hardware, applications and some recent HOW-TOs. 
I finally bought a Terratec Cinergy T2 USB Box (89 Euro) that works out of the box with Ubuntu Hoary and later. The box even has a small Tux on it, covered by the slogan "Yes, it supports Linux." :-) Just connect the box to the USB (has to be 2.0) port , attach the included antenna, scan for your locally available channels and fire up xine, mplayer, vdr etc :-) That's all. The box is powered by the host system it is connected to.

It was even harder to get the box to work under windows :-)))

I've switched to Breezy a few days ago, and it doesn't include vdr yet (in fact it does, but the package is broken because of the gcc 4.0 transition). Anyone out there who is using the box in conjunction with vdr? 

Just wanted to recommend a DVB-T receiver that just works.

Greetings Thomas


P.S.: To get the scan-utility: "apt-get install dvb-utils"[/QUOTE]
 How did you the channel scan? Which apps did you use?

---

### Post by fdimmling on 2005-08-18
[QUOTE=tvoss]Hi all,

as my TV died last week, I decided to replace it with a DVB-T receiver connected to my Aspire 1363 WLMi. I googled a few hours and finally reached [http://www.linuxtv.org](http://www.linuxtv.org). Thumbs up for this site, all relevant information especially an overview of currently supported hardware, applications and some recent HOW-TOs. 
I finally bought a Terratec Cinergy T2 USB Box (89 Euro) that works out of the box with Ubuntu Hoary and later. The box even has a small Tux on it, covered by the slogan "Yes, it supports Linux." :-) Just connect the box to the USB (has to be 2.0) port , attach the included antenna, scan for your locally available channels and fire up xine, mplayer, vdr etc :-) That's all. The box is powered by the host system it is connected to.

It was even harder to get the box to work under windows :-)))

I've switched to Breezy a few days ago, and it doesn't include vdr yet (in fact it does, but the package is broken because of the gcc 4.0 transition). Anyone out there who is using the box in conjunction with vdr? 

Just wanted to recommend a DVB-T receiver that just works.

Greetings Thomas


P.S.: To get the scan-utility: "apt-get install dvb-utils"[/QUOTE]
 I have bought the same card but get problems to scan:

fd@acer:~/DVB$ scan de-Berlin-2
scanning de-Berlin-2
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 522000000 0 2 0 1 1 2 0
initial transponder 570000000 0 2 0 1 1 2 0
initial transponder 658000000 0 2 0 1 1 2 0
>>> tune to: 522000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
__tune_to_transponder:1282: ERROR: Setting frontend parameters failed: 71 Protocol error
>>> tune to: 522000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
__tune_to_transponder:1282: ERROR: Setting frontend parameters failed: 71 Protocol error
>>> tune to: 570000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE

[ more messages like before ...]

ERROR: initial tuning failed
dumping lists (0 services)
Done.

What's going wrong?

Friedrich

---

### Post by hjt4vdr on 2006-04-25
Hi,

maybe w_scan (a tool to scan DVB-C/T channels for vdr) work's for the rest of the world, in austria it does.

[http://free.pages.at/wirbel4vdr/w_scan/index2.html](http://free.pages.at/wirbel4vdr/w_scan/index2.html)

compile it with make
cp w_scan /usr/local/bin

**english howto**
the last version is w_scan-20060216.tar.bz2
[http://www.edafe.org/vdr/wscan.html](http://www.edafe.org/vdr/wscan.html)

bye
Horst

---

### Post by wirbel on 2006-04-29
[QUOTE=hjt4vdr]Hi,
compile it with make
cp w_scan /usr/local/bin
[/QUOTE]


Inside the w_scan tarball there is already the compiled version too, compiling is only needed, if you changed the source code.

wirbel

---

