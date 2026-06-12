---
title: "Lenovo W530 and docking station"
date: 2013-02-09
forum: Hardware
---

### Post by MakOwner on 2013-02-09
I just got a new company supplied laptop and I'm having issues getting my external monitor recognized while the lap top is docked.

I was using a t61 prior to this and had no issues at all - it just worked, and when docked the external monitor was recognized.

The new dock has dual HDCP/DVI connectors and I have tried both - if the laptop lid is closed during boot, you see the boot/loading graphic display briefly on the external monitor, but it goes away as soon as the desktop comes up - if the laptop lid is open you see nothing at all on the external monitor -- and I can't find anyway to get Linux to recognize the external monitor.

Anyone else have this issue?

Stumbling around in the BIOS and I see that you can only select an alternate screen for primary boot if you select "discrete graphics".
I have done that, selected one of the ports in the docking station and now see the bios and Linux boot screen on the external monitor, however, after the grub men, the screen just goes light gray with a cursor in the upper left corner.

---

### Post by MakOwner on 2013-02-09
I have this working for me, but if I had been making the decision, I would not have this laptop.  This is what worked for me on Linux Mint (mate) 14:

Install with the BIOS setting for Graphics set to "Discrete" with the optimus option disabled.
Disable both Virtuliztion options.
After installing, do all your updates and set "nox2apic" in the grub command line (I set it as the first parameter in mine).
At this point you should be able to set up the dock connected monitor, and enable the nvidia proprietary drivers if you want.
After you get the installation stable and the video set like you like, if virtualization is important to you, you can try turning it back on after you ensure that you can boot with the nox2apic parameter.

Be careful as I have read reports where this ddin't work for some people - but it worked for me.

---

