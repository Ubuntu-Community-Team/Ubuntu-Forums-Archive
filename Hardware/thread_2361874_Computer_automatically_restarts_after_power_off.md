---
title: "Computer automatically restarts after power off"
date: 2017-05-21
forum: Hardware
---

### Post by habana on 2017-05-21
I recently installed an old SSD into an even older PC after installing 17.04 onto the SSD. There was an existing minor problem with the PC – it often beeped during the boot process but this stopped once the OS started loading. With the covers off to install the SSD I looked into the beeping problem. It was in a fact a CPU fan alarm caused by the Intel 4 pin fan stopping and starting approximately every two seconds. The voltage on the +12V line was a steady 4.7V so presumably the control line was pulsing at 0.5 Hz. I had the fan mode set to AUTO in BIOS, the solution was to set it to PWM. Why this was necessary after many years of correct operation I have no idea.

I had a few problems getting 17.04 to start but this was resolved and all was good for a few weeks. Then the PC developed a new problem. After power down (not hibernation) the computer would restart after 10-60 seconds. After establishing that the front panel switch was not faulty and checking that Power On by Mouse/Keyboard was disabled in BIOS I decided the PSU must be faulty and bought another. If I had bothered to check the PS_ON signal from the motherboard I could have saved my money as it was that signal that was triggering the restart. Anyway, I was happy to buy a new PSU as the old one was very noisy and the new one super quiet.

I next did the following, rebooting when appropriate:
[LIST]
[*]Disabled anything in BIOS related to power on, wake up.
[*]Measured the CMOS battery – 3.09V.
[*]Cleared CMOS – reloaded defaults and made minor changes, AHCI etc.
[*]Removed LAN and USB cables immediately after power off. No Wi-fi.
[*]Updated the BIOS to Ver 9A from Ver 4
[/LIST]


None of these made any difference. Finally I disabled HPET Mode in BIOS and that did the trick.

So, at last, I have two questions. What processes in Ubuntu use HPET  and how on earth does this timer cause my computer to restart?

Gigabyte GA-G33M-DS2R
Intel ICH9R chipset
Core 2 Duo CPU
Integrated graphics
Ubuntu 17.04 64 bit

---

