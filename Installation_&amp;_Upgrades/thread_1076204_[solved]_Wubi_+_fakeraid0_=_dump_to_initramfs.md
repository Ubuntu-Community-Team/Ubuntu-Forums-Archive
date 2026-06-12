---
title: "[solved] Wubi + fakeraid0 = dump to initramfs"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by gecko on 2009-02-21
Hi,

I have gone through a number of threads before posting this issue. 

I am seeing the following error when I try to select Ubuntu on the first reboot after a wubi install. Grub loads and executes its commands and I get the Ubuntu logo. Then I end up at a command prompt for initramfs with no apparent errors. Using the exit command produces many logical errors like below. I tried editing the grub boot commands, adding the phrase all_generic_ide at the end of the kernel line and it made no difference.

[number]Buffer I/O error /dev/sda1, logical block [number]

I suspect the RAID0 stripe across 2 x 320GB drives is causing the issue. What things can I try to see if I can make this work. I have attached an compressed nfo file from msinfo32 vista utility with my current system configuration.

It's an Abit AB9 using Jmicron RAID0 stripe. This is an iNTEL ICH8 SATA Motherboard with 4 SATA ports that support up to RAID5 *if* you bought the Pro version (I did not). It then has an additional 2 SATA ports controlled by the Jmicron JMB36X chipset for RAID0/1 options.
.

---

### Post by gecko on 2009-02-21
I went back to try it again and this time selected verbose from the grub install menu. Instead of the Ubuntu logo I see it detecting all the devices. Seems to pick everything up but I cant seem to pause it to check as it fly's past. Eventually I see a lot of the following error repeating before I am dumped into initramfs.

[ numbers ] attempt to access beyond end of device
[ numbers ] sda: rw=0, want 1250162688, limit 625142448

Thanks for any help you can provide :)

UPDATE: [WubiGuide]("https://wiki.ubuntu.com/WubiGuide") does say raid0/1 will be supported in 8.10 version of Wubi. Doesn't seem to work.

---

### Post by gecko on 2009-02-21
What information I can gather indicates that dmraid from the alternate CD is required to support fakeraid. Is it possible to mod the desktop iso to include dmraid?

---

### Post by gecko on 2009-02-24
[Solved]

Wubi uses desktop image for installation which does not have the dmraid software required for fakeraid drives to be recognised. The solution it to use the alternate CD to install without Wubi.

---

