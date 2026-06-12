---
title: "problem detecting second hdd through the live-cd"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by MadJestyr on 2009-04-17
My system has two hdd's on it, hd0 has ubuntu already loaded on it.  I partitioned my second hdd to two partitions (ext2) and I put the Kubuntu live-cd ISO, vmlinuz, and initrd.gz on the first partition.  I edited menu.lst as such:

title		BOOT: Kubuntu Live-CD
root		(hd1,0)		
kernel		/vmlinuz boot=casper iso-scan/filename=/kubuntu-8.10-desktop-i386.iso 
initrd		/initrd.gz
quiet

I am using the second hdd to test out differant distro's, started with Kubuntu because I am already familiar (sort of) with ubuntu.
I rebooted my computer and Kubuntu Live cd worked perfectly, until I went to install it.  Then it wouldn't give me an option for the second hdd, let alone the second partition, which is where I want to put it.  The strange part is that (through the live cd) the drives were detected through Dolphin and I could even mount them, but there was no install option for those drives on the second disk.

Can anyone help with this problem?

---

