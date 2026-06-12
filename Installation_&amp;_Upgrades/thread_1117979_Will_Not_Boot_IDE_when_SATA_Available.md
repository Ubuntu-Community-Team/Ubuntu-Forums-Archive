---
title: "Will Not Boot IDE when SATA Available"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by contax on 2009-04-06
First, I'm new to all of this.  My two and three year old have Edubuntu systems, but that is the extent of my system experience.  I've searched for an answer.. I'm sure this has been covered..but haven't found a relevant post.

I'm trying to put together a Samba file server on a new Atom 330/Intel system.  The boot drive is a 120MB IDE drive and /srv and swap partitions are on two 1.5TB SATA drives in software Raid1, ext4.  I can setup the system just fine with Server Edition 9.04 as long as I haven't any SATA devices.  When I install with the SATA available, the system tries to boot off of HD (0,1) ext4 and I know that I have my IDE setup with a separate /boot with boot flag on in a primary partition sitting at the beginning of the IDE drive and ext2.  I don't know which drive is HD (0,1), but I do know that my only ext2 partition is /boot.  Bios is set to boot off the IDE.  My error message at boot is Error 15: Can't find file.  Of course, it is looking on the wrong drive.

Can I instruct the boot system to load from my ATA /boot?  For example, is there a line command that I can add prior to the boot sequence?  I don't know why it is booting from a drive/partition without a boot flag on.  My / (root) partition as well as all other partitions are ext4.  I didn't see any other facility when partitioning for settting up /boot to run grub other than the boot flag.  Any help would be appreciated.

Thanks

---

### Post by Mark Phelps on 2009-04-06
I started with an IDE-only system.  When I added a SATA drive, the BIOS automatically selected that drive as the boot device.  When I unplugged the SATA drive, the BIOS automatically reselected the first IDE drive as the boot device.  Sounds like the same thing is happening to you.

Go into the BIOS and check the order of the hard drives.  You want your boot drive to be the first one in the list.

---

### Post by contax on 2009-04-06
Mark:

The boot order is correct.
I can physically remove the SATA drives and the result is the same.

Thanks

---

### Post by meierfra. on 2009-04-06
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD (with all you hard drive attache) and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post (use the code tags).

---

### Post by contax on 2009-04-06
The only reason that I was using IDE was that there were only two SATA ports on the motherboard.  I have decided to run a small SSD for system and one 1.5TB drive for data and more active partitions.  I'll give up the Raid 1 in that all data will be secondary backup.  In other words, the primary system and one backup would need to go before I would need the data on this server.  I know that this sounds crazy, but I have actually needed to go to secondary backups when my primary failed.

I will download the Boot Info Script to get a better understanding of what I'm doing in that I have another larger server that I need to assemble.  For now, the new system seems to be functioning and so now I need to bone up on Samba and SFTP.

Thanks...

---

