---
title: "Throttle Processor Speed"
date: 2009-06-28
forum: Hardware
---

### Post by PerfectReign on 2009-06-28
I was wondering if there was any way to help throttle processor speeds. 

I have a two-year-old Compaq nw9440 laptop, with a dual-core 2.0 ghz Intel processor and 2GB RAM running Ubuntu 9.04 / 32-bit.

When the processor load goes high - as in running Virtual Box with Vista or running Tux Racer or Tux Kart (my kids) - the machine will often run the fan high and occasionally go into ACPI shutdown. 

I have the laptop running on a laptop fan base, but this doesn't seem to help when it goes into hyperdrive.

I know there's a program for Wintendo that limits processor speed. I looked up this activity in Ubuntu and only found one post in this forum - [http://ubuntuforums.org/archive/index.php/t-475522.html](http://ubuntuforums.org/archive/index.php/t-475522.html) - as well as an old kernel bug listed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/22336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/22336)

What can I do to keep the processors from going at full speed?

Here's the laptop at normal speed:

[IMG]http://www.perfectreign.com/stuff/2009/20090628_laptop_normal.png[/IMG]

And here's the laptop running Windows 7 in Virtual box as an example...

[IMG]http://www.perfectreign.com/stuff/2009/20090628_laptop_win7_sysmon.jpg[/IMG]

Any ideas on what can be done for this?

:confused:

---

### Post by PerfectReign on 2009-07-02
Okay, figured my own problem out.

This was getting nightmarish. Whenever I'd run VirtualBox especially - but even TuxRacer or some flash-based sites - my processor would go crazy and eventually force an ACPI shutdown.

Last night, it dawned on me. The laptop is 2.5 years old. I have never cleaned out the vents.

I got out my air can, and went to town, blowing out any orifice I could find in the laptop.  Since then, it has been running perfectly, and not even causing a whine when running VirtualBox (I upgraded to 3.0x yesterday.) or TuxRacer.

---

