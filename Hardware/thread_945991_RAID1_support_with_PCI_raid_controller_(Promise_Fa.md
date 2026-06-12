---
title: "RAID1 support with PCI raid controller (Promise FastTrak TX2300)"
date: 2008-10-12
forum: Hardware
---

### Post by srpenney on 2008-10-12
I've just installed Ubuntu (8.04.1 - desktop) and my RAID1 array is not detected properly.  I'm seeing two instances of each of my partitions in the array instead of just one.  

The raid controller I am using is a Promise FastTrak TX2300 PCI raid card.  The bios on the card is set to treat the two attached 500GB drives as a RAID1 array.  

Nautilus shows me four 200GB and two 100GB partitions that I can mount when it should be showing me two 200GB partitions and one 100GB partition.  

When I use liveCD I get the same behaviour.

Does anyone know what modules I need to install to get the RAID1 array to be detected properly?

I know that this can be done because I was able to get it up and running with an older Ubuntu install that I had made (with help from IRC).  Unfortunately I was stupid and did not write down what to do.  I won't make that mistake again.

Thanks in advance for any help or suggestions,

**Update:**
I was able to get help on a forum and the steps to get it up and running are as follows:

- install mdadm using 'sudo apt-get install mdadm'
- partition drives if needed (not in my case because the drives were already partitioned)
- create the partition using 'sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1'
- mount the new array through Nautilus or using 'sudo mount /dev/md0 /media/my_mountpoint'

To have this process automated at startup:
- append the output of 'sudo mdadm -Es | grep md0' to /etc/mdadm/mdadm.conf
- update /etc/fstab with an entry for this drive similar to the command used above.

---

### Post by cariboo on 2008-10-13
You have to setup raid in the the bios of your raid controller. You should have an option to  go into the raid setup program when you boot the computer.

Jim

---

### Post by srpenney on 2008-10-13
The PCI raid controller's BIOS has already been configure to have a 2 disk array in a RAID1 configuration.  When I go into the controller's BIOS I see the array is as expected.  However, Ubuntu doesn't see it the same way as I would expect.

---

### Post by celestius on 2008-10-13
If i'm not mistaken, it would appear that the chipset on that card is a software raid not hardware so you would have to load software to get linux to see the drives the way you want. This page: [http://linuxmafia.com/faq/Hardware/sata.html]("http://linuxmafia.com/faq/Hardware/sata.html") says something about the driver being unable to be built properly for the 2.6.x kernel. Iono. Just tossin some info out there.

---

### Post by srpenney on 2008-10-14
> **celestius said:**
> If i'm not mistaken, it would appear that the chipset on that card is a software raid not hardware so you would have to load software to get linux to see the drives the way you want. 

That probably explains the installs that I had to do to get it working before.  They were likely software raid software.

I've looked around a little more and found that 'md' seems common in many places when talking about linux and raid.  I seem to recall that when I finally got the drives mounted that the showed up as /dev/mdx.  Could this be what I'm missing?

Steve

---

### Post by AlexD1979 on 2008-11-14
Hello,
I am not sure If I have the same issue. I have a Utuntu 8.04 64Bit installed with DELL PC on-Board Controller and only one Samsung 250 GB HDD. After that I add the TX2300, plug the HDD1 to Port 1 and HDD2 to Port 2 and build a RAID 1. That works fine, the Server going on works! 
But, now if I try to test some cases of failure, the Raid controller fails. e.g. I unplug the power cord from HDD 1 when the server is up and works. I see some messages on the linux console (Some lines sd 0:0:0:0 rejecting I/O to offline device, Buffer I/O error on device sda1,logical block 123123123, EXT3-fs error (device sda1): ext3_find_entry: reading directory 2777712 offset 0 and so on) and after that, I cannot access linux. After I reboot the server hard reset, everything is ok with one remaining HDD. Does this Controller not support a hot-failure if one drive became defect?
Is there a very good HowTo to get the Server wotk with "full RAID 1" functionally?

---

### Post by neorg on 2008-12-12
I think that the problem is the confusion between SOFTware and HARDware RAID. If you have a REAL hardware RAID controller than Linux only see the drive(s) as they are configured by the RAID controller.

So if you have a HARDWARE RAID controller and configured the drives to RAID 1 Linux will only see one drive.

If you have a SOFTWARE RAID controller Linux will still see 2 (all) the drives. In fact this kind of controllers are worthless if you run Linux because you still have to  run mdadm (Multi Disk). MD is *also* a software solution for RAID.

In fact  you don't need any software RAID controller is you can connect the wished number of hard disks directly to you motherboard.
  
Her is a mdadm How-To [http://ubuntuforums.org/showthread.php?t=40846]("http://ubuntuforums.org/showthread.php?t=40846")1

---

### Post by AlexD1979 on 2008-12-16
Hello,
The right "RAID-feeling" will not be provided from the Hardware-Controller. If I remove one drive by un-plug the power-cord the RAID crashes until I reboot the server. It could not be the real function of a RAID Controller only to "synchronize" the files, but also it has to provide a 100% go-on function in the malfunction of one HDD in a RAID1.

---

