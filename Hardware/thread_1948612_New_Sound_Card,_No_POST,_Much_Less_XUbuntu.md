---
title: "New Sound Card, No POST, Much Less X/Ubuntu"
date: 2012-03-28
forum: Hardware
---

### Post by etisdale on 2012-03-28
Hello. I'm hoping somebody can give me an idea of what to do here.

Background: I have a Turtle Beach Santa Cruz sound card that is being detected, but is not working under Xubuntu. All I get is a high-pitched sound. I can't adjust through alsamixer, and I can't seem to stay connected to the pulseaudio server when using related configuration tools. Apparently, there is some sort of unresolved bug. So, I did a little research and bought a new card (ASUS Xonar DG).

Problem: When my new ASUS Xonar DG card is installed, my computer will not even POST--all I get is a black screen.

The computer will POST with the old card installed, and it will do so without any sound card at all. It just will not POST with the new card.

I've gone into the BIOS and changed settings such that the BIOS only configures what it needs at boot. That is pretty much my only option in the BIOS--but I can double check next time I boot an update this post.

[[ Edit to provide update on BIOS configuration:

Boot Configuration

Plug & Play O/S		[Yes] 
Reset Config Data	[Yes] 
Numlock			[On]

For Plug & Play O/S option: No, lets the BIOS configure all the devices in the system. Yes, lets the operating system configure Plug and Play (PnP) devices not required for boot if your system has a Plug and Play operating system.

For Reset Config Data: No, does not force the PnP data to be cleared on boot. Yes, clears PCI/PnP Configuration Data stored in Flash on next boot. ]]

I have a Dell Dimension 4400 (yes, it's a little old), the specs for which are here: [http://support.dell.com/support/edocs/systems/dim4400/specs.htm](http://support.dell.com/support/edocs/systems/dim4400/specs.htm)

The specs do not indicate what PCI version I have, but it appears to be PCI v2.2. The specs indicate an Intel 845 chip set, which, according to the following site, appears to have PCI 2.2:
[http://www.intel.com/support/motherboards/desktop/sb/cs-008634.htm](http://www.intel.com/support/motherboards/desktop/sb/cs-008634.htm)

The ASUS Xonar DG, apparently, works with PCI v2.2 or above.

Any troubleshooting ideas? Any ideas for a card that will just work?

Thanks!

---

### Post by etisdale on 2012-03-28
Well, for whatever reason, I tried again before returning the sound card to the store, and it worked.

Prior to the sound card working though, I also installed a "new" video card. Maybe I made some system changes in the process and blindly stumbled into the solution; maybe I wasn't working it right to begin with. No matter, I now have audio and video!

---

