---
title: "Compatibility Question: Nvidia Geforce 940M proprietary DRIVER 16.04"
date: 2016-12-06
forum: Hardware
---

### Post by mistcloud-misty on 2016-12-06
When I first upgraded to 16.04 after it came out and tried to install the proprietary drivers it sent me into an endless login loop and would not work no matter what I tried. So I put it aside and have worked on the integrated graphics with my Intel processor. This was the older proprietary driver than the one now. I want to be cautious about proceeding, but want to utilize Nvidia because I am hoping my laptop will run cooler (runs too hot on Intel, need laptop cooler when doing anything with even slight graphics), but I don't want to have to deal with major crashing, failure of working completely, and in the worst case, having to reinstall.

Long story short: at one point I purged nvidia drivers, rebooted, and no input devices were detected and I could not, in any way, get it working again so had to reinstall. 

So basically: anyone out there with my graphics card (or similar), with the proprietary 367.57 driver through Additional Hardware found it worked? 

I'm not willing to upgrade to 16.10 yet (not until my college semester is over, at the very least...) 

Any input would be appreciated. :)

---

### Post by mistcloud-misty on 2016-12-10
Okay, so I caved, installed the proprietary driver (wouldn't work from additional drivers, strangely, and had to install through command). Slow boot, several black flickers, but I managed to login. That's a bonus. It's running a little cooler than it was previously which is great. I mean, less than 50 degrees with a game open and several additional tabs.

I'm just concerned (curious) about these errors in dmesg. Are they problematic or do they have no impact on my computer?

```
[   32.357906] vgaarb: this pci device is not a vga device
[   32.378567] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   32.378615] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   32.378641] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   32.378665] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   32.378688] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   32.378725] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   32.378748] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   32.380973] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150930/nsarguments-95)
[   32.514675] nvidia-modeset: Allocated GPU:0 (GPU-b962cbd3-dd31-bec6-e7dd-e8c274d646d4) @ PCI:0000:04:00.0
[   32.514771] nvidia-modeset: Freed GPU:0 (GPU-b962cbd3-dd31-bec6-e7dd-e8c274d646d4) @ PCI:0000:04:00.0
[   32.987631] vgaarb: this pci device is not a vga device

```

If these are just text problems that have no impact then all is good (for now, until it crashes, since that's what my laptop does best). Hopefully it works though. New programs seem to be opening slower than before, but could be unrelated.

---

### Post by oldfred on 2016-12-11
Are you using Bumblebee or just nVidia.
I thought newest nVidia replaced bumblebee.

Arch and discussion of similar errors. Seems error does not matter, but you may need a boot parameter.
[https://github.com/Bumblebee-Project/bbswitch/issues/108](https://github.com/Bumblebee-Project/bbswitch/issues/108)

---

### Post by mistcloud-misty on 2016-12-11
Just Nvidia. 

Only real problem I have run into is that normal suspend crashes the computer 100% of the time - workaround so far is pm-suspend in terminal.

---

