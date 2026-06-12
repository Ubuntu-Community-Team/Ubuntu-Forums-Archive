---
title: "Enabling MIDI input on Zoom s2t C5.1t, partial solution - need help!"
date: 2022-06-07
forum: Hardware
---

### Post by ordigital on 2022-06-07
**Device: **ID 1686:007f ZOOM Corporation ZOOM S2t C5.1t
**Recognized:** yes
**Audio working:** yes

[B]Problem:
[/B]MIDI port is visible but no MIDI control-change signals comes from footswitches after connecting audio interface.

**Partial solution:**
1. Redirect USB device to virtual manager with Windows 32bit with C5.1t ASIO driver 
2. Wait until device is started
3. Stop redirection of USB device
4. Footswitches send MIDI  control-change signals

**Thoughts:**
First I thought that Zoom ZFX plug-in is enabling midi but MIDI-OX shows zero MIDI signals (including SysEx) from application itself. 
MIDI is enabled immediately after Windows ASIO driver is loaded. When I stop redirecting USB to Windows in virtual manager it stays enabled in Ubuntu and I can use it without any problems.
That means ASIO driver is sending some signal to interface that enables MIDI messages.
I am able to monitor MIDI in and out ports after device is connected to Windows but I am unable to monitor signals that comes to device when it is being connected. 

**Questions:**
1. Is it possible to check what ASIO driver does to device that linux module doesn't?
2. Is it possible to dump «state»(?) of device and to compare it before and after ASIO driver enables MIDI out signals?

---

