---
title: "Free space on HD incorrectly reported"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by beeldings on 2006-04-26
I am running Breezy Badger x86 on an AMD Athlon 64 3000+ system. The motherboard is an ASUS K8V-MX, and the hard drive is a Seagate 160 GB connected via IDE. The motherboard's BIOS correctly detects the drive as 160 GB. During the installation process, the Ubuntu partition manager correctly detected the drive as a 160 GB drive. I partitioned the drive as follows: partition one 159 GB for "/" as Reiser, partition two 1 GB as swap. I proceed with the installation and when I loaded Nautilus I noticed that I only had 146 GB free. I loaded the System Monitor (Applications > System Tools > System Monitor) and clicked on the "Devices" tab. /dev/hda1 was listed as having 148.1 GB of total space with 146.3 GB free space, 1.7 GB were used. Now, if I had partitioned /dev/hda1 to use 159 GB of space, why is it listed as only having 148 GB?

My initial thought was that perhaps 11 GB were used when the filesystem was formatted as Reiser. However, after wiping the drive and installing Ubuntu again, I used the same partition scheme except that I used Ext3 instead of Reiser, and I still appear to be missing 11 GB. This problem isn't specific to Ubuntu, it also occurs with Linspire (which came with the computer, I would never go out of my way to buy it, but that's another topic) which is why I thought it might be with how the drive is formatted during setup.

---

### Post by graigsmith on 2006-04-26
i don't know the specifics to the internals of reiser, but it could be very likely that a certain percentage of the drive is in reserve, it would certainly improve file system operations.  i formatted all my drives with ext3.  i dont notice any missing space.

---

### Post by beeldings on 2006-04-27
I just performed a server installation of Ubuntu Breezy and upgraded from the CLI via apt-get to Dapper. Inside of creating a swap partition, the drive is formatted with one 160GB Ext3 partition with the reserved space set to 0%. However, upon restarting the computer and booting into Gnome, I noticed that the drive is once again detected as having a capacity of 146.7 GB with 144.9 GB of free space. This is more annoying than anything, however since I want to use this system as a DV workstation, I need every last byte available. I'm going to download a trial of Windows XP 64 to determine whether or not this problem is exclusive to Linux or if it occurs in Windows.

---

### Post by hw-tph on 2006-04-28
What does **sudo hdparm -I /dev/hda | grep device\ size** output? You will need to replace "/dev/hda" with whatever the device name is for your hard drive.


Håkan

---

### Post by beeldings on 2006-04-28
```

        device size with M = 1024*1024:      152627 MBytes
        device size with M = 1000*1000:      160041 MBytes (160 GB)

```

---

