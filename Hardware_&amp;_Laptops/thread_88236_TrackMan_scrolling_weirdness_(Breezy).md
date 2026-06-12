---
title: "TrackMan scrolling weirdness (Breezy)"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by jliedeka on 2005-11-09
My TrackMan scroll wheel is misbehaving under Breezy.  I have two of them and both act the same way so I think I can rule out a hardware problem.

I used xev to see what was happening.  When scrolling down for the first time after doing anyhting else with the mouse or keyboard it sends two button 5 events for each click of the wheel.  If I don't touch anything else, it sends one button 5 event for each click.  The more annoying symptom is that when I scroll up for the first time, it sends a button 3 and 2 button 4s.  Button 3 is the right click so I usually get a context menu and can't scroll until I hit escape.  If I don't move the cursor or click anything, I can scroll up with one button 4 for each click.

Relevant info -
xorg.conf:
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/psaux"
        #Option         "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "ZAxisMapping"          "4 5"
EndSection

** It was configured by the install to use /dev/input mice, I tried /dev/psaux but it didn't change anything.  I've used the imps/2 protocol under other flavors of linux with no issues.

From /proc/bus/devices:

I: Bus=0011 Vendor=0002 Product=0006 Version=0000
N: Name="ImExPS/2 Generic Explorer Mouse"
P: Phys=isa0060/serio1/input0
H: Handlers=mouse0 event1 ts0
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

From /var/log/Xorg.0.log

(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/psaux"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "false"
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

The only other thing I should mention is I'm using a KVM switch but that was never an issue before.  Any ideas?

     Jim

---

