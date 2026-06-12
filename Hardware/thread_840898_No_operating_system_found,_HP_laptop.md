---
title: "No operating system found, HP laptop"
date: 2008-06-25
forum: Hardware
---

### Post by cdtech on 2008-06-25
After spending two day's trying to get my Suspend and Hibernate configured to work with my laptop, I did a reboot to check the configuration only to find the "No operating system found" on the screen.

The first thing I thought of was a dead Hard Drive. My BIOS could not see the drive on boot, although I could boot into the drive (only to see the message though). I inserted the Live CD and took a look at the drive in question. Once I seen that I had access to the drive, I mounted the boot partition and reconfigured the Grub Bootloader (thinking it was corrupt).

Same problem after reboot. I then thought a dead sector. Before I headed out to Best Buy for another hard drive I swapped my Windows drive and placed it in the primary bay only to find the same message on reboot.

I went into the BIOS and reset to factory defaults then reconfigured to my liking. Once I did the reboot the operating system was seen. 

I just wanted to share this with others who are debating on the same issues as I was. I'm in search of an updated BIOS now.

---

