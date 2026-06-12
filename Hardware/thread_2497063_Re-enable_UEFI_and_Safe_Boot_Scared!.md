---
title: "Re-enable UEFI and Safe Boot? Scared!"
date: 2024-04-21
forum: Hardware
---

### Post by nickhacking on 2024-04-21
I hope that this isn't a stupid question.

I have a fairly modern machine (c. 2021) which is an AMD 8 core, 16 GB PC. It came with Windows 10 installed.

The first thing that I did was to set it up to dual boot Ubuntu. To do this, I had to tell the UEFI / Bios that I wanted it to behave as a "legacy" machine and ignore "Safe Boot".  This was all fine and I've got Ubuntu doing everything that I could ask of it. Currently I'm on Ubuntu 22.04.4 LTS.

When I fire up the machine, I get a Windows boot loader which asks me if I want Linux, Windows 10 or Windows 7 (ignore the last option, it doesn't work well: it's an OS from an older PC that I sort-of rescued: I never use it). If I pick Linux it starts up (I think) Grub 2- and from there I can start up Ubuntu.

All happy. All working. The system does what I want.

BUT. I hear that Microsoft is going to stop supporting Windows 10 next year, and I have a couple of applications, which only run under Windows.... To "upgrade" to Windows 11 I'll need to re-enable full UEFI and Safe Boot.

My question is: will I lose access to my Linux system? If I do, how can I get it back? I don't want to format my Linux drives and partitions and reinstall: it's taken a long time to get the system working exactly the way that I want.

All help and advice gratefully received.

---

### Post by Autodave on 2024-04-21
This a Win 11 machine with Safe Boot disabled and UEFI and Legacy allowed.  Works fine for Win 11 and Ubuntu 22.04

---

### Post by oldfred on 2024-04-21
The only real difference between an old BIOS/MBR system and new UEFI/gpt system is the version of grub.
Ubuntu will let you use the old MBR with UEFI, but probably should not. Microsoft required gpt partitioning for UEFI boot.
But if you did use MBR, conversion to gpt totally erases a drive, so be sure to have good backups.

I have a full UEFI/gpt install on my external SSD using USB. But was able to add a BIOS boot stanza on my 2006 laptop and directly boot the kernel on the external drive. It did not care that grub was UEFI on external drive as I booted in BIOS mode.
This same external SSD boots on my newer Windows 11 laptop with Secure boot on. But if I had installed in old Legacy mode it would have been more difficult to convert to Secure boot as kernel & all the boot ffiles must be the signed versions.

---

### Post by nickhacking on 2024-04-22
Thank you, both, for your advice.

Since my Ubuntu system lives on a separate drive from the boot disc, I thought I'd risk tweaking the UEFI settings, so I went back to: UEFI mode only; Windows Boot Loader; TPM 2 enabled.

Unsurprisingly, my boot options disappeared and the machine started up in Windows 10. PC Healthcheck said that my system was ready for Windows 11, so I bit the bullet and decided to install it. 8% of the way in, Windows complained that it couldn't cope with the way that I'd partitioned my disc and aborted the upgrade. I went back into the UEFI settings and put everything back to the way it was: the machine is now dual-booting happily again. My fears were unfounded.

I might do some repartitioning of the boot drive, one day, to let Windows 11 install but for now I've had enough. October 2025 is a way off yet.

---

### Post by MAFoElffen on 2024-04-23
The thing "is", which no one mentioned, and you don't seem to realize... Was that when you installed Ubuntu, you could have left the BIOS boot mode as UEFI instead of changing it to Legacy... And it would have installed Grub2 in that UEFI mode.

To have it reinstalled in that mode, it is still possible, but now you have some work ahead of you to do that.

When you say "safe boot"... Are you combining terms? Do you mean "fast boot", "secure boot", or "safe mode"?

---

