---
title: "SD card won't automatrically mount."
date: 2009-07-07
forum: Hardware
---

### Post by soucmaster00 on 2009-07-07
I've tried the instructions [on this page]("http://wiki.answers.com/Q/How_do_you_mount_sd_card_in_ubuntu_eee_without_superuser_rights") but they didn't work. Any help? I have Jaunty Jackelope, if that's any help.

---

### Post by shatterblast on 2009-07-07
As a warning, this is only a suggestion.  Please back-up your data safely.  You might try formatting your SD card to a FAT32 partition.  Doing so will erase your information.

---

### Post by soucmaster00 on 2009-07-08
I've tried formating, but what I found out I need is a partition table recoverer. Know a good one I can use on my SD card?

---

### Post by shatterblast on 2009-07-09
For command-line utilities, there is FSCK.  "Testdisk", found within Synaptic, features robust partition repair capability.

For software in a window, GParted (also known as "Partition Editor" under Administration) from Synaptic has a "Check" function that may do the job.  It probably uses FSCK anyway.

---

### Post by soucmaster00 on 2009-07-13
My SD Card does not appear in GParted, and also, I fixed my SD card using Windows Vista's Partioning software. Score one for Vista. Where does this leave us? 9 X 10^10000000000 to 1, Ubuntu?

---

### Post by shatterblast on 2009-07-13
Some USB devices are Windows-compatible only in nature and may take up to 2 years or more sometimes to reach compatibility with Linux.  The difference is that it tends to be free in the open source community.  For examples, phone and music-playing devices in general need such attention.  In essence, you pay Microsoft for speed of which you receive technology, but you also get the bugs that come along with it.

---

