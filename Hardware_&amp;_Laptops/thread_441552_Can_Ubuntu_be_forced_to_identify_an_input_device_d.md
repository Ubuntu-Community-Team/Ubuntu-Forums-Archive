---
title: "Can Ubuntu be forced to identify an input device differently?"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by johnrader on 2007-05-12
Users of various touchpad input devices are unable to get the linux Synaptics driver applied to them. They function as mice, but that's all. If Ubuntu could be forced to identify these touchpads as "AlpsPS/2 ALPS TouchPad", this might solve the problem.

As I understand the issue:

Synaptics, the company, is the major provider of touchpads for portables. The Synaptics driver for linux makes the extended touchpad features and adjustments available under linux. This driver has been expanded to cover Alps touchpads, a lesser but significant provider of touchpads for portables. Alps touchpads for portables implement the technology of Cirque, which makes its own touchpad devices, and licenses the technology to other device makers, like Adesso.

The problem is that while the Synaptics driver functions with Cirque based touchpads by Alps, it doesn't with Cirque's own touchpads, or Adesso keyboards, or Fellowes touchpads - I have one of each. None of the non-Synaptics/ Alps touchpads are recognized by Ubuntu as touchpads. As the Synaptics linux driver Trouble-Shooting Guide states: "The touchpad must be identified a "SynPS/2 Synaptics TouchPad" or an "AlpsPS/2 ALPS TouchPad". If it is identified as a "PS/2 Generic Mouse" or "PS/2 Synaptics TouchPad", something is wrong."

Assuming these non-Alps Cirque-based pads are producing touchpad output, is there a solution to getting the Synaptics linux driver applied to them in forcing Ubuntu to identify them as "AlpsPS/2 ALPS TouchPad"? If someone could come up with the instructions I'd gladly test them on my touchpads.

An example of the cat /proc/bus/input/devices output for a Cirque based touchpad:
I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input5
H: Handlers=mouse2 event5 ts2
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0

An example of an Alps identification to which the Synaptics linux driver can be applied:
I: Bus=0011 Vendor=0002 Product=0008 Version=7322
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse2 ts2 event3
B: EV=f
B: KEY=420 0 670000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

---

