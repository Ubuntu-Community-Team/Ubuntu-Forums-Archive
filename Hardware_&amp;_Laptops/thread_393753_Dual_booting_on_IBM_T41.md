---
title: "Dual booting on IBM T41"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by elbeanio on 2007-03-26
Hi All
I've got ubuntu installed on 3 machines and happily multi-booting with various operating systems on 2 of them. This damn T41 is causing me huge headaches; ubuntu is great on it, all the hardware is detected straight away and even WPA is relatively easy to get set up. The problems start when I try to dual boot it with XP

I install windows and leave 20 gig empty for ubuntu, then once windows is installed I install ubuntu. As soon as I've finished installing ubuntu and reboot into windows it starts loading the drivers and about 3 seconds in it bluescreens with an "unmountable_boot_volume" stop error.

I've heard of this problem elsewhere and it seems to be related to the hidden partition and windows thinking that the partition table is wrong but I've switched that off in the bios and reinstalled twice since. Same thing happens each time, also if I boot back into ubuntu the xp partition has an exclamation next to it in gparted stating that the filesystem can't be read, is that normal for an NTFS partition?

Has anyone else had problems with this? I need windows on the laptop for writing software but want to keep linux on it in case I need it. At the moment it's looking like I'm going to have to either run windows in a VM but with only 512mb ram i'm not keen or should I just give up on using ubuntu and install xp on its own.

Cheers
Ian

---

### Post by elbeanio on 2007-03-26
Ok, just in case anyone's interested here goes.

To fix it I created 2 partitions in the xp installer and installed windows on the first. Then I booted into the ubuntu live cd and ran gparted. Turns out the there's a 3GB empty space at the end of the disk where I assume the hidden bit was. I used the whole 3GB hidden partition for the swap and deleted/recreated the second win partition. After that I rebooted and windows works fine.

I think probably windows was creating partitions based on a 34GB disk, not counting the 3GB "hidden" partition even though I've got it disabled in the BIOS. So when I came to install ubuntu it ignored the fact that the partition was hidden (as expected) and created a partition across it. When I booted back into windows it must've seen the partitions were bigger than the disk and crapped itself.

Hope that helps someone else, I noticed other people have also had this problem but never came across a solution.

---

