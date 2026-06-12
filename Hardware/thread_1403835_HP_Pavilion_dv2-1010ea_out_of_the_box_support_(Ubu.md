---
title: "HP Pavilion dv2-1010ea out of the box support (Ubuntu 9.10)"
date: 2010-02-10
forum: Hardware
---

### Post by arranmc182 on 2010-02-10
Here is a list of what hardware works out of the box

Graphics card: Works
Sound Card: Works
Network Card: Works
Bluetooth: Works
Wifi: Dose Not Work
Track Pad: Works
Multi Card Reader: Works
USB Ports: Works
Internal Mic: Works

To get the WiFi card to work connect a Ethernet cable to the laptop and wait a moment then Ubuntu should show a notification that there is drivers available for hardware. If that dose not work go to software sources & go to the third party software tab and make sure all is ticked and then go to Updates tab and make sure Proposed Updates are ticked, Then open Synaptics Package management and search for Braodcom what you need is there.

It seems like this laptop dose not fully work with APIC & ACPI so it will not read the battery properly it will give a percentage but not time remaining.

There is a problem with the built in WiFi & some routers with WPA2 if you find problems try changing to WPA.

---

### Post by brian10161 on 2010-02-11
I'm going to be trying 9.10 on my DV2-1044CA today. It has the ATi Radeon HD3410 in it, and I think a broadcom WiFi adapter. 

I'll post my results here.

---

### Post by adm1968 on 2010-03-13
> **brian10161 said:**
> I'm going to be trying 9.10 on my DV2-1044CA today. It has the ATi Radeon HD3410 in it, and I think a broadcom WiFi adapter. 

I'll post my results here.
[FONT="Georgia"]How did it go, then? ;)[/FONT]

---

### Post by tamran on 2010-06-23
> **brian10161 said:**
> I'm going to be trying 9.10 on my DV2-1044CA today. It has the ATi Radeon HD3410 in it, and I think a broadcom WiFi adapter. 

I'll post my results here.

I guess since there was no reply, I'll put my two cents in.

I recently picked up one of these laptops (also the 1044ca model).  I gave both 9.10 and 10.04 a try and 10.04 worked like a dream with this laptop with the following two exceptions:

1) The microphone does not seem to work at all. Neither did plugging in an external microphone in the mic jack.

2) APIC (or ACPI??) drivers aren't working.  It does not do power management at any acceptable level.  Unplugged for 15 minutes drained the batter to 77%.

The power management was so bad I just can use (this is an ultra portable machine after all).  So I had to put windows 7 back on it. I'll be watching closely to see if anything changes because it really did run well when plugged in.

Tamran

---

