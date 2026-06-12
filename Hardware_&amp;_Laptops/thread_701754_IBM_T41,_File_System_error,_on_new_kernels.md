---
title: "IBM T41, File System error, on new kernels"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by baoqing on 2008-02-19
Hi There,

I recently installed Gutsy (7.10 - kernel 2.6.22.14) in a T41, which works perfectly.

However, problems arises when I installed other kernel versions (tried both 2.6.23.16 & 2.6.22.18, got both from kernel.org, in order to have at least one other working kernel to play with and to test out my own drivers, thought 23.16 and 22.18 should be stable enough).

Problem description:
1) rebooted (to either of the new kernels), file system check error occurred in /dev/sda5 (which is my /home partition), fsck failed. Here are the messages during booting process:
"/dev/ sda5 contains a file system w. errors, check forced.
Error reading block 6447415 (Attempt to read block for files syste, resulted in short read)
/dev/sda5: unexpected inconsistencyl RUN fsck manually (i.e. wihtout -a or -p options)
fsck died with exit status 4   [failed]
"
Boot procedure was able to continue from this point on, but since /home partition (sda5) is failed during checking, I can't log in to my account.

2) however, when I reboot to the exisitng known working Gutsy (7.10), it could fix the file system problem. Here is the log:
"
Log of fsck -C -R -A -a
Tue Feb 19 15:40:54 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sda1: clean, 48/554208 files, 272358/2257100 blocks
/dev/sda5 contains a file system with errors, check forced.
/dev/sda5: 102557/3541440 files (11.3% non-contiguous), 1331281/7078632 blocks
"
reboot succeeded and I have no problem log in to the system.

3) If I rebooted to my new kernel (22.18, or 23.16), right after shutdown from Gusty, new kernels are able to reboot and everything works fine. The file system error arises only after I reboot again after I shutdown from either of the new kernels. Seems like the new kernels have rewritten some of the system file setting somehow after they ran. (or Gusty fixed/ignored the problem during boot?)
Here is an example of my testing sequence:

boot to Gutsy -> succeeded
-> reboot to 2.6.23.16 (new kernel from kernel.org) -> reboot succeeded ->shutdown and reboot
-> reboot to 2.6.23.16 again -> failed in sda5 file system checking
-> reboot to Gutsy -> fsck checking sda5 (/home) -> reboot succeeded
-> reboot to 2.6.23.16 -> reboot succeeded
-> reboot to 2.6.23.16 -> failed on sda5 checking

Having been a long time RedHat user (however haven't tried redhat in this T41), and recently switched to Ubuntu, I wonder if Ubuntu Gutsy has modified something so the file system errors were ignored/fixed? 
or if I missed something that I should've set up during kernel configuration, or perhaps I should set some fsck parameter, or somewhere such as in menuconfig to fix this?

Any suggestions in tracing/fixing this problem will be much appreciated.
Thanks in advance.

-Baoqing Ye

---

