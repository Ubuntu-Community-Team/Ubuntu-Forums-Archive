---
title: "Intermittent crashing on start-up at different points"
date: 2008-07-11
forum: Hardware
---

### Post by Fhtagn on 2008-07-11
Heya,

I've just installed Ubuntu 8.04.1 on a new laptop, dual booting with Vista. (The laptop's an Advent 5302, with standard off-the-shelf specs).

I've had a rash of cases of Ubuntu failing to load, but these only occur intermittently.  The two main incidents are that it reaches "Starting Bluetooth" and then just hangs, never getting to [OK].  I've tried aborting to a prompt with Alt-Ctrl-F2 and stopping it manually and that just hangs.

At other times, it reports "hda_codec Unknown model for ALC662" and again hangs.

When it does load, my USB mouse sometimes works and sometimes doesn't. On those occasions when the mouse doesn't work (I've not checked when it does), opening a terminal and using lsusb just hangs the terminal.

I've already added the "noapic nolapic acpi=off irqpoll pci=irqroute" to the boot line, since without the first three it doesn't boot and without the last two, the mouse never works.

I've looked on these forums and via google, and frankly, the intermittent nature of the problems worry me.  Can anyone suggest anything?

Fhtagn

---

### Post by ajgreeny on 2008-07-11
If you have no bluetooth devices, just disable bluetooth at boot up using **bootup manager** (bum) from synaptic and see if that helps.

---

### Post by Fhtagn on 2008-07-11
> **ajgreeny said:**
> If you have no bluetooth devices, just disable bluetooth at boot up using **bootup manager** (bum) from synaptic and see if that helps.

I've disabled it via "Services" which seems to have worked (The department computer guy wandered past so I bent his ear for a bit).  Cheers.

---

