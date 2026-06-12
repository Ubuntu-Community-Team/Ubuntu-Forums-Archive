---
title: "Install Grub always hangs"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by Steveha1 on 2005-12-13
I am new to Linux but desperately wish to use it.
I have a home built PC that runs Windows XP Pro.
The MB is a Gigabyte GA-G8gnxp Pro Duo
I have two Seagate Sata 200GB drives configured as Raid1 that contain 
the XP system.
I have installed another drive: Seagate Sata 80GB for the Ubuntu system.
The two Sata 200GB disks show as SCSI1 in the partition config part and the 
SATA 80GB disk shows as SCSI2.  I have set the Ubuntu partitions automatically: main partition is 74Gb and the Swap is 3GB.
When I try to install Breezy it gets to the 'Installing Grub Package' and then 
just hangs there forever. After re-booting I get 'Error unable to load operating system'.  I then have to disconnect the 80GB disk or delete the partitions then XP will load.
I have gone through the BIOS settings but cannot see anything that locks the MBR and I have even removed the two raid disks but always get the same problem.

Any help would be most appreciated.
Steve

---

### Post by Steveha1 on 2005-12-16
During my attempt's last night I had the unusual occurance of apt failing to install.  when i clicked 'Continue' Grub then detected that I had windows XP installed and asked me if I wanted to install Grub on the MBR.  I said no because of the failed apt,  Now it's back to Hanging on 'Installing Grub Package'.  I can do ALt+F2 to go to a command line if that is of any help.

Kind rgds, Steve

---

### Post by humandoing on 2005-12-16
Hey Steve,

I basically got screwed like this, too. I have 2x 160GB SATA disks, and wanted to install Ubuntu on another 120GB SATA disk. I have an ASUS A8V Deluxe motherboard.

I ended up getting booted into the OS (after that dreaded "Error loading operating system") and mucked around with the grub configuration files for 2 days before giving up.

I went to the store and bought an IDE disk - and BAM! Everything works a charm.

Right now, unfortunately, that would be my recommendation to you in order to get it all to work. I've felt your pain :(

-daniel

---

### Post by ZylGadis on 2005-12-16
That is not a panacea either, I'm afraid to report. I am currently trying to install kubuntu on a machine that has two 5400rpm IDE drives. The master (40GB) is taken up by windows, as I want to play civ4 :) I've been trying to install kubuntu on the slave (120GB), trying all kinds of partition combinations. The install hangs at "Installing GRUB boot loader" every time.
I wonder if it is not a bad cd. I had the infamous "bsdutils" problem a month ago when I put ubuntu on a laptop, which was solved by mounting a ubuntu .iso instead of the cd. I guess this is the next step to try now.
If it does not work, I'll try putting windows on the slave drive and kubuntu on the master one.
Any help would be appreciated in the meantime.

---

### Post by ZylGadis on 2005-12-16
Update: just made it past the "install grub" point. Solution: used the master drive to install Kubuntu on. Now the master has a windows partition, an ubuntu partition, a linux swap partition, and (supposedly) grub in the MBR. The slave is not partitioned at all, I'll probably make it a FAT32 file repository.
We'll see how it behaves from here. Right now it is at 40% of "Installing Packages".

---

