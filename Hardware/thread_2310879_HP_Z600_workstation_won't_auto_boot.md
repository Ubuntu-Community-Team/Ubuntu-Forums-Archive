---
title: "HP Z600 workstation won't auto boot"
date: 2016-01-22
forum: Hardware
---

### Post by c-cubed on 2016-01-22
I can't get the workstation to auto boot after power failure.

I am running an Ubuntu 14.04 LTS on an HP Z600 workstation.
The machine bios is    786G4 V0.3.54
Using F10 Setup
I have enabled Advanced BIOS Power On for all days of the week.
I have enabled Advanced Device Options Wake on LAN.
I have enabled Always ON as the option after power fail.

If I:
1. Boot the machine
2. Pull the plug on the workstation
3. Plug the workstation back in

It does not boot. The power remains off and I have to push the button on the front to reboot.
If I wait until the time the Bios Power On should turn the machine on, it doesn't.

Any ideas.
This box is being used as a remote server, so I have to get it to auto boot after power failure.):P):P

---

### Post by c-cubed on 2016-01-23
Is it possible this behavior is a result of some interaction between Ubuntu 14.04 LTS and BIOS? All the BIOS versions on HP web site are OS specific. The machines boots fine to either Windows 7 64-bit Professional or Ubuntu 14.04 LTS 32 bit. I have only tried the power loss auto boot from Ubuntu and as I described it doesn't work. Is it possible Ubuntu is not properly initialize some hardware or memory location that BIOS uses to determine the run state? I can imagine that this might be possible for behavior relating to auto boot following power loss. But I can't imagine how it could be possible for the BIOS Power on feature. In truth I have a hard time imagining its related to the OS. When the power is off from unplugging or by pushing the power button, the OS is dead. When power is restored the  only thing active is the BIOS. If it is set to Advanced->Power Options->Always on, it seems to me it should start the boot cycle. It doesn't.

Hmm maybe just for laughs I'll boot Windows 7 Professional and try the power off sequence.

---

### Post by c-cubed on 2016-01-23
Getting closer. I found some information in Wikipedia regarding ACPI interface. Its says "Once an OSPM-compatible operating system activates ACPI, it takes  exclusive control of all aspects of power management and device  configuration. The OSPM implementation must expose an ACPI-compatible  environment to device drivers, which exposes certain system, device and  processor states." Is it possible that the OS versions I'm running or the BIOS version are some how incompatible and not properly interacting through ACPI?s 

Come on guys, surely one of you GURU's has some experience or knowledge of ACPI and can tell me if I'm on the right track.

---

### Post by c-cubed on 2016-01-26
Yet more research and testing but still no resolution.


I  tried booting to Windows 7 Professional 64 bit to see if it would  automatically boot after power loss. It did not. Same behavior as Ubuntu  14.04LTS. No reboot, I had to push the power button on the front.



I  found documentation on ACPI under Ubuntu which says unless over ridden  by command line parameter the Ubuntu kernel masquerades as Windows for  ACPI interface. This seems consistent with the behavior I'm seeing.



Is there a better place to post this? Is there a forum focused on BIOS and/or ACPI?

---

### Post by c-cubed on 2016-01-29
Additional information.
I originally installed Windows 7 professional 64 bit and Ubuntu 14.04 LST 32 bit on an HP Pavilion DV7 laptop.
The lap top failed and couldn't be repaired.
I bought a used HP Z600 workstation with no OS.
I moved the disk drives from the failed pavilion to the Z600.

It booted Windows 7 successfully the first time I poweredZ600. Windows automatically updated itself including a number of drivers.
Windows 7 Professional 64 bit boots and runs fine on the Z600. The only problem is it won't auto boot after power failure.

Ubuntu 14.04 LTS 32 bit booted successfully the first time I selected it on the Z600. I used update manager and selected upgrade.
Ubuntu 14.04 LTS 32 bit boots and runs fine on the Z600. The only problem is it won't auto boot after power failure.

Basically after a power failure the machine acts as if the power off button was pressed. This is for both a power fail in Windows and/or a power fail in Linux.
It appears that even though "Always On" is set in BIOS and BIOS Power On is selected for all 7 days of the week. They are not doing anything.

Any ideas?

---

### Post by c-cubed on 2016-02-03
Really disappointed that no one has any ideas on this.

---

### Post by c-cubed on 2016-02-06
Changed nothing and issue disappeared.
Had a 4 hour power failure.
Machine successfully automatically rebooted when power was restored.

So just pulling the plug on the Z600 and then restoring power does not reboot.
Power fail on Z600, router, monitor DOES reboot.

---

