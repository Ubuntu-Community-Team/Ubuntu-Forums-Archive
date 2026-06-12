---
title: "HP C6280 + Duplex Printing + Remote (Network) Print Job"
date: 2008-05-19
forum: Hardware
---

### Post by torstenaf on 2008-05-19
**The Problem**
The duplex printing option does not work when the print job is to a remote printer. The print jobs always come out single-sided.

**The Setup**
I have an HP C6280 printer connected to a headless printer/server (an Aopen MiniPC). The printer has an automatic duplexing feature. I primarily print remotely from my laptop to the headless print server. My laptop has Kubuntu installed.

**Local Printing Works - Single/Duplex**
I can remote desktop from the laptop into the printer server to print local jobs. I can successfully print duplex or single-sided jobs to the printer. I simply choose single-sided or duplex in the print dialog.

**Single-Sided Remote Printing Works**
I can print to the remote print server from my laptop. Single sided works just fine.

**Duplex Remote Printing Fails**
When I try to specify the duplex option in the printer dialog, the print jobs still come out single sided. I tried printing from Adobe Acroread, Firefox, and a straight postscript file. Always single-sided. For some reason, the choice of duplex does not transmit across the network.

**Forcing Duplex in Local Options Works**
If I remote desktop in and set the local printer preferences to duplex, then all my print jobs come out duplex. This includes local and remote. This situation is not ideal, since I generally prefer single-sided with occasional duplex.

**Help!**
How can I get CUPS to recognize the duplex option for remote print jobs (not just local)?

---

