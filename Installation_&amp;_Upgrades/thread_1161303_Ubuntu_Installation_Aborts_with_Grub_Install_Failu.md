---
title: "Ubuntu Installation Aborts with Grub Install Failure."
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by ScaryBob on 2009-05-16
This is a major issue (for me) that has been around since 8.04 and still exists in 9.04. It has happened repeatedly on different systems with different versions of Ubuntu. It is probably an installer bug or may be a grub bug. It has stopped me from adopting Ubuntu and continues to do so. I've found references to it by searching the internet but no solution. 

The system:
1. Asus M2N-E motherboard. 2 GB RAM. Yada, yada, yada. Primary hard drive is a 120GB SATA with 3 primary partitions and 1 extended partition. The first three partition contain WinXP SP3, Ubuntu 9.04 and Mandriva 2009. The fourth is divided into Linux swap and a /home partition for Ubuntu. There are also 10x500 GB SATA drives connected to Syba cards on the PCI bus. This is an MDADM RAID5 array created with Mandriva.

The end result: Install fails with a grub installation failure. The live CD kicks out to the live desktop with an incomplete installation. The alternate install disk lets me finish the installation but does not install the grub boot block or menu.

Possible contributing issues:
1. The Ubuntu installer does not appear to correctly recognize the primary hard drive in the BIOS. (There are some other side effects but I will stick to the current issue.) Instead, it recognizes the SATA Syba connected drives first and assigns them as sd[a-j]. The primary drive is assigned sdk instead of sda. This may be an issue for grub if it is trying to install the boot block on sda. It also messes up the RAID array since it is defined to be on sd[b-k].
2. I've seen this problem before. The common factors appear to be multi-booting from the primary hard drive and the existence of two or more physical hard drives, one or more of which are on third party controllers, usually some sort of RAID.
3. The Ububtu installer does not recognize the MDADM RAID array. (Note that Mandriva does recogize the array and configures it during the install.)

What I am trying to accomplish:
1. Have the 120GB drive (recognized as primary by the BIOS) be installed as sda.
2. Have the 10 Syba connected drives installed as sd[b-k], as originally defined, and assembled as md0. (I can do the assemble manually after the installation.)
3. Get the grub boot block and menu installed correctly.

TIA for any help.

---

### Post by hal8000 on 2009-05-17
You have a similar problem to me. In my case live CD boots correctly but installation of 9.04 fails at 94% and never installs grub or the kernel.

If the live CD boots you may be able to copy the working kernel and initramfs to a flash drive, or mount one of your other linux systems from thr live environment and copy the files across.

An alternative fix may be to boot into Mandriva, mount the Ubuntu root partition and check to see if the kernel and initramfs have been copied into /boot, then to modify Mandriva grub and boot that way.

---

### Post by ScaryBob on 2009-05-21
I did manage to boot Ubuntu by modifying the Mandriva grub boot menu. However, I want to migrate to Ubuntu so that is not seen as a long term solution. This has happened to me every time I have tried to install Ubuntu on a system that has more than one drive. The grub installer fails because it tries to put the boot record on the wrong disk or gets some internal error. What is needed is an advanced option for the grub install and a look at the way the Ubuntu installer handles disks. I believe there is a way to change the disk order but haven't looked into it. However, it would be better if this was also built into the install as an advanced option.

I have some professional experience writing installers with Unix but that was a few years ago. Unfortunately, I don't have enough knowledge about Ubuntu (yet) to fix this. First, I need a working system but every Ubuntu distro and workstation I try, I get the same failure. Plain vanilla systems (with one drive) seem to install Ok but that is not typical of my workstations.

---

### Post by hal8000 on 2009-05-21
Disk order in grub is controlled by the file /boot/grub/device.map


Heres mine from PCLinuxOs 2009

[anc@localhost grub]$ cat device.map
(fd0) /dev/fd0
(hd0) /dev/hda
(hd1) /dev/sda

hd0 is mapped to /dev/hda as I have both IDE and SATA.

In my Jaunty install, the installed halted at 94%, grub was never written and neither was the kernel or initramfs. I'm not getting much help from the forum yet, so will have to keep trying.

I agree with you, it would be better if either the install had more user control over grub.

---

### Post by presence1960 on 2009-05-21
> **hal8000 said:**
> Disk order in grub is controlled by the file /boot/grub/device.map


Heres mine from PCLinuxOs 2009

[anc@localhost grub]$ cat device.map
(fd0) /dev/fd0
(hd0) /dev/hda
(hd1) /dev/sda

hd0 is mapped to /dev/hda as I have both IDE and SATA.

In my Jaunty install, the installed halted at 94%, grub was never written and neither was the kernel or initramfs. I'm not getting much help from the forum yet, so will have to keep trying.

I agree with you, it would be better if either the install had more user control over grub.

There is an option when installing which allows you to choose where to place GRUB. See attached screenshot. Bottom right just above 3 buttons there is an "advanced" button. Click it and you can choose where to install GRUB either to any partition or MBR.

---

### Post by semi-newbie on 2009-05-22
> **presence1960 said:**
> There is an option when installing which allows you to choose where to place GRUB. See attached screenshot. Bottom right just above 3 buttons there is an "advanced" button. Click it and you can choose where to install GRUB either to any partition or MBR.

Where do I find this option in the server install of Ubuntu 9.04 to override where Grub is installed to?  It's all text, there's no graphics.  I have a very similar problem: BIOS is set to boot off a PATA drive, also have two SATA drives that I configure during Ubuntu 9.04 (and 8.10 tried too) install as RAID 1 with LVM on top.  The installer goes and writes Grub to one of the SATA drives, trashing its partition table.  The only partition on any drive that I set to be bootable was the partition on the PATA drive that I mount as /boot, why Ubuntu would install GRUB overtop its own RAID stuff I have no idea.

This problem has occurred on THREE different computer systems, each with a small (8-20Gb PATA drive, and two 500Gb SATA drives).

---

### Post by presence1960 on 2009-05-22
I have never used the server install, but someone who has will come along to answer.

---

### Post by ScaryBob on 2009-05-23
Thanks for the hint about device.map. I will look into it. Maybe I can fix it up after the fact.

I have similar problems with the desktop install, both live disk and alternate. As far as the install goes, the issue is that grub is either installed on the wrong disk or it fails due to some unknown condition that causes a write failure. I have tried different options for where to install grub. It makes no difference to the failure in Jaunty.

---

