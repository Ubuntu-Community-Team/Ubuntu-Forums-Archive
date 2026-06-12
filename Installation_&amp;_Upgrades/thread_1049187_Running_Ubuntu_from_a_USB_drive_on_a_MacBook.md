---
title: "Running Ubuntu from a USB drive on a MacBook"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by toMeloos on 2009-01-24
I've been issued a MacBook (v4.1) from work. It's fine but I want to use Ubuntu for personal use. I prefer the GNOME interface over MacOS, want to run software that's not freely and legally available for MacOS, etc.

Before I was running Ubuntu from USB on a Lenovo ThinkPad which worked great. I want to do the same thing on this MacBook but this seems to be a lot more difficult due to Apple using EFI in stead of BIOS. One important objective is to be able to boot from USB without altering the MacOS installation on the regular hard drive. This means not installing a bootloader like REFIT on the hard drive, but on the USB drive instead. Also, I want to run a full installation on my 32 GB drive, not one of those compressed bootable-CD like solutions that make permanently installing additional software and changing system settings difficult.

I've read just about any forum thread, blog entry and howto I could find on Google but haven't been able to get it working. Anyone here that can tell me how to do this?

Thans!

---

### Post by cosine352 on 2009-01-24
have a look at this one

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by toMeloos on 2009-01-24
Sorry, that doesn't help me very much. Besides BIOS versus EFI there is also a MBR versus GPT issue.

Getting this to work on a traditional computer using a BIOS and MBR for disks was easy. Apple however is using the newer EFI for booting and GPT for disk partitioning, which linux does not seem to be equally equipped for.

---

