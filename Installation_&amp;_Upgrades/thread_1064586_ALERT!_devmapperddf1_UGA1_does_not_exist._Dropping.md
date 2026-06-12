---
title: "ALERT! /dev/mapper/ddf1_UGA1 does not exist. Dropping to a shell!"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by gwalker2104 on 2009-02-09
Hi I am hoping someone will give me a hand. I Installed 64-bit Ubuntu Server v8.10 on a computer that has an Adaptec HOSTRaid array configured RAID1. The Ubuntu installer correctly detected the array and appeared to install everything there.

When Ubuntu boots up, I get the error ALERT! /dev/mapper/ddf1_UGA1 does not exist. Dropping to a shell!

Well, UGA is the name of the array I built in the BIOS of this computer.

I did some searching around on this forum and discovered that if I type dmraid -ay at the (initramfs) prompt and then press CTRL-D, then Ubuntu finishes booting normally.

Now this server is intended to be installed in a remote data center so it is totally unacceptable to have to type this command in every time the server is rebooted. I either need to figure out how to automatically execute the command dmraid -ay at bootup or determine the root cause of this error so that it will not happen.

Someone else suggested putting a timeout in the kernal command in the menu.lst file. I tried that, but the only thing that happens is a longer delay before I get the error.

I tried a few other kernal parameters pointed out on these forums, but none of them worked.

While I have been searching these forums, I have been downloading the huge Fedora installed. I guess I will try that next unless someone has another quick suggestion to try with Ubuntu.:(

---

### Post by gwalker2104 on 2009-08-04
No help here. I gave up on Ubuntu and went with Windows Server 2008. It installed and ran perfectly on the first attempt.

---

### Post by Fredvs79 on 2009-08-05
I solved my issue.
  I used a different kernel. Instead of patching the 2.6.23 vanilla kernel with the RTAI patch for x86, i386 or x86_64, I saw that RTAI-3.7.1 supports the 2.6.29 kernel for i386 and powerPC architectures.
  I got the 2.6.29 kernel, and patched it with the x86 patch, compiled it and it loaded fine.

I conclude that either
1) the bug is with the 2.6.23 kernel, or 
2) that I patched the 2.6.23 kernel with the wrong architecture patch, and I got it right for 2.6.29.4

---

