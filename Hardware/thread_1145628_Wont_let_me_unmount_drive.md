---
title: "Wont let me unmount drive"
date: 2009-05-01
forum: Hardware
---

### Post by kakarotman on 2009-05-01
So i run dual sessions of gnome and kde and i just deleted my vista partition because i was dualbooting and i want to make my linux partition bigger but it wont let me unmount my linux partition. Here is My Partitions info:

Partition        filesystem     mountpoint     size               used               unused
-------------------------------------------------------------------------------------------------------
/dev/sda1      ext3                                      1.46 GiB       57.82 MiB        1.41 GiB 
unallocated   unallocated                          80.01 GiB          ---                    ---
/dev/sda3       extended                             67.58 GiB          ---                    ---
     /dev/sda5  ext3                                     7.81 GiB        2.12 GiB          5.69 GiB
     /dev/sda6  linux-swap                           3.90 GiB            ---                   --- 
     /dev/sda7  ext3                                     5.58 GiB        273.73 miB      5.31 GiB
     /dev/sda8  ext3                     /               48.20 GiB      18.32 GiB         29.88 GiB
     /dev/sda9  linux-swap                          2.10 GiB             ---                    ---
      

I want to know what partitions on here i need to keep so as not to screw my ubuntu and kubuntu up.  I triple Booted PCLinuxOS, Ubuntu, and Vista untill i deleted vista which is what that unallocated chunk of partition is.  
        Every time i try to Unmount my /dev/sda8 which is my ubuntu partition it says this:

"The partition could not be mounted from the following 
mountpoints:

 /

Most likely other partitions are also mounted on these 
mountpoints. You are advised to unmount them manually."


        How can i unmount this and get that unallocated chunk of memory to be added to it? And what partitions should i delete to get rid of my pclinuxos?

---

### Post by drs305 on 2009-05-01
Any partitioning work done on / will have to be done from the LiveCD. You cannot perform partitioning operations on a mounted partition, and of course your system is mounted if you are currently using it. 

You only need one swap partition, no matter how many ubuntu/kubuntu distros you set up. Techinically, you don't even need one swap partition, but I won't get into that discussion.

Make sure your grub and fstab files correctly reflect the correct partitions once you have finished partitioning. The device names (sdXX) and/or the UUIDs may have changed.

These commands can help determine the settings.
```

sudo fdisk -l
sudo blkid
sudo ls -l /dev/disk/by-uuid

```

---

### Post by kakarotman on 2009-05-01
oh duh k thanks i will try that. Will it delete anything? cuz i need to know if i need to back my stuff up.

---

### Post by drs305 on 2009-05-01
> **kakarotman said:**
> oh duh k thanks i will try that. Will it delete anything? cuz i need to know if i need to back my stuff up.

Anytime you are partitioning you should make sure to back up your important data. Most users have found gparted (Partition Editor) very reliable but accidents do happen.

The chances of losing data are less than those that you will have to make some tweaks to fstab and grub to get your system to reboot. In the latter case, it will just take a bit of file editing to get things working. If the former, how mad will you be if you lose the data and didn't have it backed up?

---

