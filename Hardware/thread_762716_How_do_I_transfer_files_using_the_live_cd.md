---
title: "How do I transfer files using the live cd?"
date: 2008-04-22
forum: Hardware
---

### Post by bwallum on 2008-04-22
I need some help. I have been trying to help a forum member backup files from a corrupt hard drive.

The harddrive is boot and runs grub. Grub starts Ubuntu and then fizzles about a quarter of the way along the start up bar.

Using a live cd the user wants to back up files on the defective harddrive to an external harddrive.

However he gets a message saying there is no room on the external hard drive when he is convinced there is a good 20GB left.

What is the size limit of file that can be moved within the live cd environment?

Can he use a simple command to shift the relevant files rather than knife and fork them all?

---

### Post by bingoUV on 2008-04-22
External hard drives are at times formatted with FAT32 with pitiable 4GB file size limit. Are you hitting that limit?

---

### Post by Mark_in_Hollywood on 2008-04-22
I'm the (hapless shlub) about whom the above thread starter writes. 
In answer to your question, no, I have used GPArted to partition and format the external drive. It is 20 gig and large enough for my /home.

GPArted does say the disk has no "disk label" and when I try to give it an msdos label, it "sort of works". More: Using the LiveCD to run GParted, from the terminal, calling gparted, loads first libparted and the gparted. In the terminal, libparted talks about not liking the disk label, but once the partitioning/formatting is completed, the disk shows (and I've done several) as 20 gig or 59 gig or the correct space available.

---

