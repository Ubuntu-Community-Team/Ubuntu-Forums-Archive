---
title: "Recommended PCIe SATA Controller"
date: 2011-09-10
forum: Hardware
---

### Post by asayler on 2011-09-10
Hello,

I'm in the process of building a new lab server that will run Ubuntu. I'm planning on configuring the server to use Linux software RAID5 (md). As such, I am looking for a good, inexpensive, SATA PCIe controller that is capable of operating in a straight AHCI (non-RAID) mode and exporting all connected disks directly to Ubuntu for use in the software RAID.

I know there are a whole slew of issues trying to use propriety fake-RAID drivers that come with most SATA PCIe cards in a Linux environment (especially when I just want direct access to the underlying drives for use in an md RAID setup). That said, I'm having trouble finding a non-RAID PCIe SATA controller. Many SATA controllers offer a JBOD option, but I don't know if this still requires the propriety fake-RAID drivers or not.

Do most SATA cards support a way to bypass the need for these propriety drivers and use them in a vanilla AHCI mode (like toggling between fake-RAID and AHCI modes in most motherboard SATA controllers)?

If not, can anyone recommend a good 4 to 8 port SATAII controller that I can run in a PCIeX8 slot that will work with Ubuntu out of the box and provide me direct access to the connected drives for Linux software RAID use?

I'm using a new 1155 Asus Mobo that supports the use of ASUS PIKE cards. The [PIKE 2008]("http://www.asus.com/Server_Workstation/Accessories/PIKE_2008/") would be a nice choice, but I can't seem to find any info on Ubuntu or Linux compatibiliy without having to use it's fake-RAID drivers.

Any suggestions would be appreciated. I just need an inexpensive, robust, and simple way to add 4 to 8 SATAII drives for incorporation into a Linux MD software RAID5 array.

Thanks,
Andy

---

### Post by asayler on 2011-09-10
There is a similar question floating around here if any one has suggestions: [http://ubuntuforums.org/showthread.php?p=11238560#post11238560](http://ubuntuforums.org/showthread.php?p=11238560#post11238560).

---

