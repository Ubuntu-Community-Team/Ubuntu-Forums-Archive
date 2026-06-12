---
title: "Echo Audiofire 12 - not working"
date: 2013-01-08
forum: Hardware
---

### Post by ampetrosillo on 2013-01-08
Hi everyone,

I've just installed Ubuntu 12.10, it's a pleasure to see that the UX is getting smoother, but, just as I expected, my audio interface won't work :(

...and to think that I bought an Echo Audiofire thanks to its (presumed) compatibility with Linux :D

Anyway... of course the Audio settings panel doesn't feature my Echo interface at all, so I thought, I'll install FFADO... I couldn't find the base package in the software center, so I just installed FFADO-mixer, assuming that it would install FFADO as a dependency.

And so it seems, but... when I fire up the FFADO mixer, the following error message comes up:

```
[COLOR=Red]14:29:59 logginghandler: Could not communicate with the FFADO DBus service...[/COLOR]
```I can't remember where, but I found some info on this error message, suggesting that I run ffado-dbus-server, so I did, but...

```
ERROR: messagebuffer not initialized:  Discovering devices...
ERROR: messagebuffer not initialized: 13232015453: Warning (ieee1394service.cpp)[ 375] initialize: Could not set SPLIT_TIMEOUT to min requested (1000000)
ERROR: messagebuffer not initialized: 13232015532: Warning (ieee1394service.cpp)[ 379] initialize: Set SPLIT_TIMEOUT to min requested (1000000) did not succeed
ERROR: messagebuffer not initialized: 13232331507: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
ERROR: messagebuffer not initialized: 13232331689: Error (fireworks_device.cpp)[ 217] doEfcOverAVC: EfcOverAVCCmd command failed
ERROR: messagebuffer not initialized: 13232331775: Error (fireworks_device.cpp)[ 738] readFlash: Flash read failed for block 0x00008000 (64 quadlets)
ERROR: messagebuffer not initialized: 13232331846: Error (fireworks_session_block.cpp)[ 129] loadFromDevice: Flash read failed
ERROR: messagebuffer not initialized: 13232331899: Error (fireworks_device.cpp)[ 427] loadSession: Could not load session block
ERROR: messagebuffer not initialized: 13232331950: Warning (fireworks_device.cpp)[ 367] buildMixer: Could not load session
ERROR: messagebuffer not initialized: 13232332287: Warning (efc_avc_cmd.cpp)[  90] deserialize: Deserialization failed
ERROR: messagebuffer not initialized: 13232332390: Error (fireworks_device.cpp)[ 217] doEfcOverAVC: EfcOverAVCCmd command failed
ERROR: messagebuffer not initialized: 13232332427: Error (fireworks_device.cpp)[ 624] getClock: Could not get clock info
Errore di segmentazione (core dump creato)
```[of course I'm Italian, that's a segfault anyway]

So I tried to examine ffado-test ListDevices' output:

```
adriano@adriano-Ubuntu:~$ ffado-test ListDevices
Cannot create thread 1 Operation not permitted
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x0014865e75918c0e  0x00001486  0x0000AF12   Echo Digital Audio - AudioFire12
[COLOR=Red]ERROR: messagebuffer not initialized: 13288066660: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 1 on port 0[/COLOR]
```There are two fw devices in /dev:

```
adriano@adriano-Ubuntu:~$ ls /dev/fw*
[COLOR=SandyBrown]/dev/fw0  /dev/fw1[/COLOR]
```By the way, when I run ffado-test, the IEEE1394 LED on my audio interface lights up, but nothing else happens.

I've tried searching the 'Net, but there are no clear instructions on how to fix this. My interface's firmware should be one of the latest ones, and I wouldn't like to downgrade, but it seems that my interface should still work on Linux with the latest firmwares, albeit crippled (only 44.1k-48k sample rate).


Can you help me out?

---

### Post by ampetrosillo on 2013-01-09
Anyone?

---

### Post by Yellow Pasque on 2013-01-09
[http://subversion.ffado.org/ticket/360](http://subversion.ffado.org/ticket/360)

---

### Post by ampetrosillo on 2013-01-09
So, basically, there isn't a fix? (Apart from downgrading the firmware, which is a risky endeavour, apart from being less than ideal?). Pity...

---

