---
title: "Bluetooth GPS"
date: 2009-01-05
forum: Hardware
---

### Post by bbftsoftware on 2009-01-05
Has anyone gotten gpsd to run successfully using a Pharos (iGPS) Bluetooth GPS receiver under Linux (Ubuntu 8.0.4). If so, I would be interested in learning how you were able to do this.

I might also mention that my desktop has a BT dongle plugged in.

tia,
-chance.

---

### Post by savanik on 2009-02-11
I'm doing a similar setup, and feel like I'm getting somewhere...

I'm using 8.10, which is a challenge, since apparently the Bluetooth capabilities are... more interesting in the new version. However, I've gotten the device to both detect and connect via Bluetooth. Now I'm just working on getting gpsd to recognize the device properly.

I have a feeling that there's some config file somewhere to edit to tell the thing, 'Use NEMA instead of trying to pretend this is a garmin'. Haven't found it yet, though.

Sincerely,
Sav

---

