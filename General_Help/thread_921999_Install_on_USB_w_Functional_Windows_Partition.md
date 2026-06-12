---
title: "Install on USB w/ Functional Windows Partition"
date: 2008-09-16
forum: General Help
---

### Post by Crazy_Train on 2008-09-16
Hi, I'm still new to the Linux life style. I have been using predominately Ubuntu since January this year. Now to what the post is about.

I have a 16GB flash drive that I want to install Ubuntu 8.10 (not make it act like a live disk, so I can install programs), but I need 10GB to be FAT32 so I can put my tools onto it for work (computer technician). When I use Gparted or terminal fdisk, I can make the FAT32 partition but it wont make the mbr so Windows (specifialy XP Home/ Professional) can mount the partition. In a nut shell I want:

5GB ubuntu 8.10 + updates and other software
1GB swap
10GB FAT32 for my software tools

I also know my sizes wont be 100%. Now I have been google.com/linux for about two days now and I am about to give in. So I came here before giving up. Is there a way to install Ubuntu 8.10 on the drive and have that extra partition mountable in Windows, or not (sigh).

BTW the reason I am trying to do this is in the cases of file moving with premissions, virus issues (clamtk), or check Windows drivers vs hardware issues. That and I do not want to carry CDs when I can carry one thumbdrive. Thank you so much.

---

### Post by AWerner32 on 2008-09-16
you are going to probably need to have a fat16 partition as a boot partition and mark it as bootable and install grub there. the ubuntu installer can actually do that. just create a fat16 partition as the first partition, mark it as bootable, and have it mount at /boot. make sure grub installs there (that's under advanced at the last tab of the install menu (or at least it was in 8.04)). it seems doable. I use ubuntu on my desktop but i actually have a slax distro on my flashdrive. The reason for the fat16 partition is I found that most BIOS's won't boot to fat32 unfortunately. I may give it a try tonight because i have an extra 8 GB flash drive that needs something on it. If I do end up getting to that I'll report back. In theory if the BIOS will boot to USB and your mbr and grub settings are right then it would be the same really as booting to any drive. Good Luck and report your expiriences

---

### Post by mrsteveman1 on 2008-09-16
> **AWerner32 said:**
> you are going to probably need to have a fat16 partition as a boot partition and mark it as bootable and install grub there.


You shouldn't need to do that, if grub is installed directly to the bootsector of the usb stick (no partition selector in the MBR), then there isn't any issue. The bios should jump right into the grub code regardless of the partition.

If you really want to install a full installation to the stick, i would suggest you forgo swap as a separate partition and just make a swap file after installation if you REALLY need that extra space, because swap on usb is going to be dead slow.

My suggestion is to go through the ubuntu installer normally, let the partitioner set things up with the sizes of partitions you want, but make your ubuntu partition ext3.

After that it should work fine.

Note however that Windows doesn't always like USB sticks that have actual partition tables or more than one partition, and it might not want to read the 2nd one. If that is really important to you and you find that it doesn't work with multiple partitions i suppose you COULD actually install the system to a single fat32 partition on the stick, which would be readable from windows, but this isn't the best way to run Linux.

---

### Post by Crazy_Train on 2008-09-16
> **mrsteveman1 said:**
> ...i suppose you COULD actually install the system to a single fat32 partition on the stick, which would be readable from windows...

Did not think about installing w/ Fat32. Worst case scenario I'll do that. Time is not pressing so I can try different things. My only problem with the Fat32 Linux combo, Idiots who come behind you and pull it out. How many times could that happen before the O/S mess up?! Anyways I appreciate the responses mrsteveman1 and AWerner32. Also did not take in account swap would be slow. My only worry is XP machines with 256mb RAM. with out Swap = O/S crash, right?

---

### Post by mrsteveman1 on 2008-09-16
> **Crazy_Train said:**
> Did not think about installing w/ Fat32. Worst case scenario I'll do that. Time is not pressing so I can try different things. My only problem with the Fat32 Linux combo, Idiots who come behind you and pull it out. How many times could that happen before the O/S mess up?! Anyways I appreciate the responses mrsteveman1 and AWerner32. Also did not take in account swap would be slow. My only worry is XP machines with 256mb RAM. with out Swap = O/S crash, right?

True, because fat32 has no journal (not even metadata), yanking the stick out would leave it in a partially unclean state i suppose. It really isn't a good idea to run linux on fat, but it would probably work :D

If the machine only has 256mb of ram you are going to be pushing the limit if not shooting right over it without running anything at all with Ubuntu. You can put a swap file if you need to, it will work and keep things from crashing (the currently in use stuff should stay in ram anyway). You might want to test the stick to see how fast it can read and write like this:

```
sudo hdparm -t /dev/sdX
```

that shows the approx. read speed

write tests are destructive in this case so do it on the drive while empty

```
sudo dd if=/dev/zero of=/dev/sdX bs=5M count=10
```

that will write zeros to around 50mb of the stick and tell you how fast it was able to write at the end.

I would say that a write speed of at least 20MB/s would be fast enough for swap to be OK, but its still slow and its still not the best to write to a usb stick constantly (though you'd have to write A LOT to break one).

Before you install anything though, partition the stick with one ext3 and one fat32, then see if windows can read the fat32 partition. If it can, leave it like that because thats the best configuration for you if you want to be able to write to the thing in windows.

---

### Post by C.S.Cameron on 2008-10-06
The only way I've managed to keep a FAT32 partition readable by windows is to first format the drive in FAT32 then install Ubuntu leaving a bit of the fat.
You can do this using Guided partitioning ... use remaining space or manual install.

---

### Post by snowpine on 2008-10-06
+1 the fat32 partition should be the first partition on the drive, otherwise windows won't be able to see it. :(

---

