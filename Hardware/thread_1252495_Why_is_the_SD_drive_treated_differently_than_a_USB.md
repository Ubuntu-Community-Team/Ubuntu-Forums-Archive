---
title: "Why is the SD drive treated differently than a USB drive?"
date: 2009-08-28
forum: Hardware
---

### Post by evbrown on 2009-08-28
Hello,

I have a 4 Gb 701 EeePC, running the Base version of EeeBuntu (based on Ubuntu 9.4).

I just purchased a 16 Gb AData Class 6 EeePC SDHC card from NewEgg. Since this SDHC card was labeled EeePC edition, I assumed it was the safe purchase for my 701. Unfortunately, that has not proven true.

When I tried to write to the SD card, it would copy the first file, then hang. Apparently under Linux, the card is mounted as a root privileges device. When you are logged in as a user, you don't have sufficient privileges to write to the drive. I tried sudo nautilus to change the permissions on the device, but those changes would not take. Some messages on forum.eeeuser.com suggested that the SD card needs to be formatted to ext2. I tried that, but the reformatting process hung. I waited for hours before I canceled the process. The SDHC card became inoperable and is now totally unrecognized by my EeePC. I have returned it to NewEgg for a RMA replacement.

Here is what I don't understand. My EeePC running under Linux recognizes USB drives just fine. I can read, write, and execute programs from USB drives with no problem. Why is the SD card treated differently? This seems really strange. What good is your 16 Gb SDHC card if a user can't write to it?

When I get my replacement, what is the reliable fix? Specifically, how can I get this SD card to be treated the same way my USB drives are treated?

Thanks,

---

