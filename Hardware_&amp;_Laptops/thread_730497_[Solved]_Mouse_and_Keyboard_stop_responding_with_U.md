---
title: "[Solved] Mouse and Keyboard stop responding with USB KVM Switch"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by jsprag on 2008-03-20
**Problem: ** Ubuntu 7.10 Gutsy would not respond to USB keyboard and mouse when connected and switched through a KVM switch.

**Symptoms:** 
1. When KVM was selected to Ubuntu box upon bootup, keyboard and mouse would work fine.  Once the KVM was switched to the other computer and then back to the Ubuntu machine, the mouse and keyboard would not respond.  
2. Lights on keyboard (Caps/Num/Scrl Lock) would not light up or change state.  
3. Keyboard/Mouse would work fine on other machine when KVM was switched back over to it.

**Solution:** 
1. Computer was re-booted and BIOS settings were entered (by pressing DEL key at startup).  
2. Settings for "USB Keyboard Support" and "USB Mouse Support" were changed from default setting of "Disabled" to "Enabled".  
3. Settings were saved and the computer was allowed to re-boot and enter Ubuntu normally.

This may or may not solve your USB KVM switch problems depending on your exact hardware configuration.  If you cannot find identical settings for the USB keyboard and mouse, try hunting around in the BIOS to find something similar.  If in doubt, make only one change at a time before rebooting and testing.

[U]
Hardware in use:[/U]
Logitech G5 mouse
Microsoft Office Keyboard
Gigabyte AMD64 X2 motherboard with Award BIOS
Startech Starview SV231 USB KVM Switch

---

