---
title: "EFI bootup freeze on Aspire 5560"
date: 2012-05-04
forum: Hardware
---

### Post by immerohnegott on 2012-05-04
SO, after a rough couple of days learning the ins and outs of UEFI and installing Windows 7 to a GPT disk using a ghetto-rigged generic install media, I now have a sort-of-working dual-boot setup  on my new laptop (aforementioned Aspire 5560-SB613, AMD A8 APU). The issue now is that in both Precise and Win7, the system hardlocks at bootup every other attempt, and at shutdown (though, when choosing "Restart" in Ubuntu, it drops out cleanly).

As this issue occurs in both operating systems, I'm going to go ahead and assume it has something to do with Acer's implementation of UEFI. Now, has anyone uncovered a workaround for this mess in Ubuntu? Forcing non-UEFI boot of install media is not an option, as I don't see any switches for it in BIOS. 

Also, the pre-installed Win7 didn't exhibit these issues, but it wasn't set up to boot in UEFI/GPT, just standard MBR.

---

### Post by Akita on 2012-05-22
I think you'll notice that it dies on every other reboot. If you do a shutdown it'll freeze. Hold the power key until the system shuts off and then power it back on. It'll boot just fine from a cold start. Same behavior on mine and I just installed the latest firmware (1.17 IIRC) and both OSs still do the same thing. I'm with you, it's a Phoenix/Acer issue. I also have not found a way to force BIOS/compatibility mode (should be possible on the Taino but Acer doesn't seem to have added the option). 

Forcing MBR usage should work but I haven't dug up a way to get Ubuntu to do that either (can't say I've looked very hard ... been to busy trying to get UEFI to work).

---

### Post by immerohnegott on 2012-05-23
Thanks, but I got it figured out a while ago. Should you decide to give up on UEFI, I discovered that if you remove the efi directory from the Ubuntu installer (either make a USB stick and remove it, or modify the iso) it'll boot fine in MBR mode and install GRUB-pc instead of GRUB-efi.

---

