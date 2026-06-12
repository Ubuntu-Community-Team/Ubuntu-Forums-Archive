---
title: "Wubi does not work on SafeBoot encrypted partition."
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by gmoore777 on 2009-03-24
I have this Dell Latitude D630 laptop with Windows XP on it.
The Windows partition is encrypted with SafeBoot.

I can shrink the encrypted partition successfully using a product called Acronis Disk Director Suite 10.0. (I posted an earlier thread about that).
And then I can install Linux if I wanted to.

But I instead wanted to see if I could install Linux on the C:\ drive via the WUBI installer.
The benefit would be that the data in the Linux "partition" would be encrypted since it would reside as a regular file on the Windows SafeBoot-encrypted partition. That would be cool if it works.

After the first reboot, I get to the infamous (initramfs) prompt.

Windows has been shut down gracefully, but I still did the chkdsk /r anyways. No help. I did replace "quiet splash" with "all_generic_ide" in the kernel command line of the grub menu.
No help. 
cat-ing out casper.log, I get: something about can't find the .ISO image under /ubuntu/...

C:\boot.ini was correctly read and the 2 choices of
Windows or Ubuntu is given to me, and it gets to the Grub menu. This implies that enough of the SafeBoot de-encryption drivers were loaded. But I think this may not the case since I can't get any further.

With the Acronis software product (or scheduling to run chkdsk at the next reboot), I noticed that after reboot, I see the Windows banner for 10 seconds, then the blue screen where Acronis finishes its install/repartitioning, (or chksk do its thing). So a lot more gets loaded for chkdsk and Acronis than
for the ubuntu installer. I am surmising that this extra loading of drivers is what is preventing me from going any further with this Wubi installer.

There is no way to turn off the SafeBoot encryption temporarily.
(at least I'm not privy to that capability)

Unrelated SideNote: I had to run `.\wubi.exe --32bit` else it wanted to install the 64 amd version. It also ignored the .iso image that
I had in the same directory and wanted to connect to the Internet to get the installation files.

---

### Post by avtolle on 2009-03-24
IIRC, the Wubi Guide explicitly states that Wubi will not work with encrypted drives.

---

