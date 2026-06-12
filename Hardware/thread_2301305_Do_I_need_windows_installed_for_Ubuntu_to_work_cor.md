---
title: "Do I *need* windows installed for Ubuntu to work correctly?"
date: 2015-11-01
forum: Hardware
---

### Post by MetalMusicAddict on 2015-11-01
I am about to build a new home server. I have built several new desktops that dual boot. However, one didn't work correctly until I *put* windows on it. Will I have any issues with newer motherboards on a Ubuntu-only system? Im just concerned as the old system is BIOS.

---

### Post by Bucky Ball on 2015-11-01
No. If the motherboard is UEFI only and doesn't handle the older mode, simply install Ubuntu in UEFI. Not sure what happened with your other wonky dual-boot, but Ubuntu definitely doesn't need Windows installed under any circumstance that I know of. 

Good luck. :)

---

### Post by weatherman2 on 2015-11-01
You should not need to install Windows at all.  I have installed Ubuntu on many motherboards/drives that have never had Windows on them.

The only reason I can think of that might help get Ubuntu installed correctly by installing Windows would be UEFI/secure boot.  Perhaps installing Windows in your case configured something that was not configured in the motherboard EFI or something that then allowed Ubuntu to be installed.

Also, sometimes updating the motherboard BIOS/EFI is easier if you have Windows installed.  But that doesn't mean you wouldn't be able to install Linux.
 
In the case where you have trouble installing Ubuntu, I would try to troubleshoot it and make it work instead of just installing Windows.  If you don't want to install Windows, you might start by disabling Secure Boot if that's possible on your motherboard.  That would eliminate some possible issues.

---

