---
title: "Update-Grub failed Ubuntu won't boot"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by ska8tdude on 2008-12-18
Please forgive me if this thread is in the wrong section, but I believe this should go in the Installation forum.

I have a Gateway P-6831FX Laptop with a Raid0 configuration (2x 250GB HDD). I downloaded the Ubuntu 8.10 Alternate CD (I read that the alternate CD was the easiest way to work with Raid) and partitioned my drive with Partition Magic in Windows XP. I started installing with the Alternate CD and everything went fine until it started to install GRUB. It got to Update-Grub then it failed with a fatal error. So I chose to continue with no bootloader and finished the installation. 

Now I can't boot into Ubuntu nor can I access my Windows installation (since there is no bootloader installed). I tried to use the fixmbr and fixboot commands from the Windows Recovery Console to access my Windows install, but that hasn't worked.

I'm very new to Ubuntu and Linux in general so I don't know many of the commands or terminology, but I was hoping someone could offer a suggestion on how to get GRUB installed properly or at least be able to boot into Windows XP. I'd like to not reinstall Windows XP, but if it is absolutely necessary then I suppose I will have to do that. I don't have any super important files on my XP install but would like to keep the files I do have it possible. 

If you need anymore information please tell me what you need and I'll do my best to provide the needed information. Thank you for taking the time to read this post, and hopefully we can figure this out.

---

### Post by upchucky on 2008-12-18
look for advanced supergrub, it can fix the bootloader for both win and linux.

while you are searching a very handy live disk to have is knoppix, with these tools you can fix just about any os

---

### Post by caljohnsmith on 2008-12-18
Have you by chance seen this tutorial yet:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

It usually takes special steps to install Grub to a RAID setup. If you want to boot Windows in the meantime, you could try using the Super Grub Disk that upchucky suggested. It's also possible to restore a Windows MBR to your Windows drive via the Ubuntu Live CD, so let me know if you would like to do that. I would recommend downloading a Live CD, because using the Live CD is usually the easiest way to troubleshoot these types of problems.

---

### Post by ska8tdude on 2008-12-18
> **caljohnsmith said:**
> Have you by chance seen this tutorial yet:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

It usually takes special steps to install Grub to a RAID setup. If you want to boot Windows in the meantime, you could try using the Super Grub Disk that upchucky suggested. It's also possible to restore a Windows MBR to your Windows drive via the Ubuntu Live CD, so let me know if you would like to do that. I would recommend downloading a Live CD, because using the Live CD is usually the easiest way to troubleshoot these types of problems.

I have the 8.10 Live CD already downloaded and ready to boot up, and have used it a little bit. If you wouldn't mind giving me instructions on how the fix the MBR with the Live CD that would be great. I will also take a look at Super Grub. Thank you both for the replies.

---

### Post by caljohnsmith on 2008-12-18
OK, from the Live CD, first open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -l
```
And that should show your drives labeled as sda, sdb, etc. To install a Windows equivalent MBR to drive sda for example, you would do:
```
sudo lilo -M  /dev/[COLOR="Blue"]sda[/COLOR] mbr
```
Probably installing a Windows MBR to sda will be enough since you most likely boot the sda drive on start up. If not, you can install a Windows MBR to sdb or whichever drive gets booted on start up. Also, please post the output of the above commands so I can get a better idea of your RAID setup. Let me know how it goes. :)

---

### Post by ska8tdude on 2008-12-18
Alright here is the output for the first command "fdisk -l"

ubuntu@ubuntu:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb

Disk /dev/sdc: 1002 MB, 1002438144 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e178

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         122      978912    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(120, 254, 63) logical=(121, 222, 36)


Here is the output for the second command "sudo lilo -M /dev/sda mbr"

ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.

I hope I did it right, as I'm not really sure what the outputs mean.

---

### Post by caljohnsmith on 2008-12-18
You have to run fdisk as root, so please be sure to put "sudo" in front of the command. How about trying again and post the results of:
```
sudo fdisk -l
```

---

### Post by ska8tdude on 2008-12-18
Sorry about that, should have read more carefully. Here is the output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Unable to seek on /dev/sda

```

That surely doesn't look good..

---

