---
title: "Multiple monitors - trying to get three working"
date: 2019-03-05
forum: Hardware
---

### Post by jdiazaz on 2019-03-05
Running Lubuntu (LXQT desktop) 18.10 on a Lenovo ThinkCentre.  The PC has a single DisplayPort connector and a single VGA port. I have two Acer displays(22 & 23) that are HDMI and VGA, and a Dell 19 that is DVI-D and VGA.

If I run one DIsplayPort-to-HDMI cable to one of the Acer's and a VGA to the Dell, I can get Dual monitors to work(xrandr says VGA & HDMI).  I've picked up a single DisplayPort to Dual Displayport adapter, and now I'm trying to get it to play nice

Hooking up two dp-to-hdmi and one VGA gets me two blank Acer's and one Dell  (xrandr only shows VGA)
Hooking up only the two Displayport-to-HDMI displays gets me two monitors displaying the same screen (xrandr shows a single DisplayPort)

If Lubuntu/LXQT *can *do three displays, any suggestions?

Thank you.

---

### Post by DuckHook on 2019-03-05
Welcome to the forums, jdiazaz.

The issue is not Lubuntu; your issue is the physical connections. You need an *active* DisplayPort adapter to run two monitors. A *passive* adapter will only duplicate your display (as you are discovering). Active adapters are rare and expensive. I have only found them online (not available from my otherwise well-stocked computer store). This is because they aren't in high demand. Most people running multiple monitors are running them from multiple (but dedicated) ports: one monitor to one port (I used to run four monitors, but my GPU has two DisplayPorts, one HDMI and one DVI-D).

The methodology behind daisychaining two monitors using DisplayPort is complex and arcane. See the following: [https://www.displayport.org/cables/driving-multiple-displays-from-a-single-displayport-output/](https://www.displayport.org/cables/driving-multiple-displays-from-a-single-displayport-output/)

Your DisplayPort output must be version 1.2. On most older GPUs, it is only v1.1, in which case, you are out of luck. Special adapters can be purchased that split off the DisplayPort signal to HDMI/DVI. I don't know of any that split to VGA. These are on top of the active adapter. The whole get-up ends up costing an arm and a leg and makes the enterprise expensive, unwieldy, brittle and unreliable.

Last but not least, your GPU may be resource limited and therefore unable to drive all of the resolutions and outputs needed to sustain three monitors. Daisychained DisplayPorts are quite resource-intensive. You would have to read the specs on your GPU, your monitors and the various adapters you purchase. It's a juggling act getting them all to talk to each other and play nice.

I don't want to be discouraging, but I've found that the whole attraction of multiple DisplayPort monitors is more promise than reality. However, you may be able to succeed where I&#8212;frankly&#8212;gave up.

Good luck!

---

### Post by jdiazaz on 2019-03-05
I'm kind of at the 'well, I have two working, so be happy' point.  As a Linux newbie, I wanted to try and get some knowledge before throwing my hands in the air and saying 'too much work for too little reward'.

---

