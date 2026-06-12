---
title: "Moving existing hard drive to new laptop. Will it work?"
date: 2013-05-21
forum: Hardware
---

### Post by akulbe on 2013-05-21
Current laptop: Dell Latitude D630, 8GB, 180GB SSD, Nvidia display.

New laptop: Lenovo Thinkpad W530, 32GB, Nvidia Quadro K1000M.

I have Xubuntu 13.04 all configured on the Dell. I'd really rather not have to start over from scratch with the Thinkpad, when it gets here.

I know there's a difference in the new Nvidia display card, but I also know that the new unit has an integrated Intel 4000 display adapter too. Here's to hoping the BIOS/EFI/whatever has an option that lets me pick a fixed video card, one or the other... and doesn't keep me in dynamic mode, because I hear the switching cards is problematic. Anyways... that's a tangent.

I'm wondering if the Ubuntu kernels are modular enough that I ought to be able to simply move this drive over to the Thinkpad, and most everything will just work? Am I just dreaming, or is that realistic?

Thanks in advance!

Aaron Kulbe

---

### Post by prodigy_ on 2013-05-21
Should work just fine.

---

### Post by oldfred on 2013-05-21
If a new computer it will be UEFI with secure boot and gpt partitioning. But you should be able to reconfigure to BIOS/CSM/Legacy mode and boot old drive.

Just be sure to turn off secure boot, fast boot in UEFI and in Windows quick boot or any hibernation. Some systems cannot get into UEFI except thru Windows unless those settings are off.

---

### Post by Mark Phelps on 2013-05-21
I believe the integrated Nvidia/Intel video is called Optimus -- which presents some problems in Linux.

You would be safer if you removed any proprietary video drivers BEFORE you moved the drive. At least that way, you should get some useful display when it first boots into Ubuntu.

---

### Post by deadflowr on 2013-05-21
> **Mark Phelps said:**
> I believe the integrated Nvidia/Intel video is called Optimus -- which presents some problems in Linux.

You would be safer if you removed any proprietary video drivers BEFORE you moved the drive. At least that way, you should get some useful display when it first boots into Ubuntu.

+1

I've moved drives from system to system and the only time things bork is when the OS has proprietary drivers.

Moving with only the open-source drivers results in seemless action.
At least for me it's been.

---

### Post by akulbe on 2013-06-01
Thankfully, the W530 had the option in BIOS to lock the display adapter to Nvidia. And both laptops already had Nvidia cards in them, so I already had the Nvidia drivers installed.

The move was flawless. Everything worked out of the box.

---

