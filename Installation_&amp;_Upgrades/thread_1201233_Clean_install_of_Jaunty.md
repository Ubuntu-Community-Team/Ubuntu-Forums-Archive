---
title: "Clean install of Jaunty"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Pen Spinner on 2009-06-30
I have ubuntu 8.10 installed with a separate /home partition. I have been messing with the OS and I want to start over.  Could anyone kindly give me exact directions for the "managing partitions" step of the installation when performing a clean install of Jaunty? Thanks!

---

### Post by raafaell on 2009-06-30
when managing the partitions, you have the right to create "extra" partition, so you can save files in it.. so the next time you format your computer, you will still have those files.. in that partition.. when doing a fresh installation of ubuntu.. you will need to create a partition with "ext3", and when doing this one, you may choose the size,(more than 10gb AT least in my opinion), also if I'm not wrong, you'll need to use > / as command line i think.. and then you will need to make a swap partition, with at least 300mb..

---

### Post by Sef on 2009-06-30
For a clean install do the following:

1) **Back up your data.**  There are no 100% guarantees that all will go well.

2) You will need to manually partition.   
a) delete the root partition
b) reformat the root partition as ext3, the default or other if you so choose.
c) set it up as root.

3) Are you using a Live CD or the alternate cd?

>  as command line i think.. and then you will need to make a swap partition, with at least 300mb..

You just need to reformat the root partition.   If there already is a swap, then it will be reformatted too automatcially.   A swap is not needed with enough memory, unless you want to use suspend or hibernate.

---

### Post by starcraft.man on 2009-06-30
> **Pen Spinner said:**
> I have ubuntu 8.10 installed with a separate /home partition. I have been messing with the OS and I want to start over.  Could anyone kindly give me exact directions for the "managing partitions" step of the installation when performing a clean install of Jaunty? Thanks!

Note Before: Backup all life or death data, because, life happens!

If all you want to do is install right over your current partition, just boot up the installer you used (probably live one) and follow until you get to partitioner. Once there, ask for manual control. At the next screen you'll see your partitions. Should have one for root, one for home, and any others (you should know which), just select the root one and edit it, set it to be formatted (nothing left), to use the EXT3/4 FS (whichever you used) and set the mount point to root. Next select the home partition and edit it, on this one just set the partition to mount to /home, (also ensure it's labelled as correct filesystem, i.e. if you used EXT3 before make sure it says such at the FS box). That's it, I assume you have a swap, no need to edit or mount those as you should know, it's just scratch partition.

No complications really, easy as pie. Also, I'd just like to note Jaunty is out, your free to stay with an old version, I'm just pointing it out.

Have a nice day.

Edit: My typing must be slowing down....

---

### Post by Pen Spinner on 2009-06-30
Do I delete the root or just format it over?  Also, I dual boot with windows, so do I have to label that partition as /windows or something?  I have sda1 as dell utility partition, sda2 as windows xp, sda3 as recovery, sda5 as intrepid ibex, sda6 as swap, and sda7 as /home.  When I delete sda5, the swap becomes the new sda5 and /home becomes sda6.  Will this delete or change any data in \home?  Thanks for the replies!

---

### Post by Pen Spinner on 2009-07-02
Anyone know :confused:?

---

### Post by dryphi on 2009-07-11
I have the same question - will this install method delete the current contents of /home?

I'm trying an install today so I will let you know if I figure it out...

---

### Post by merlinus on 2009-07-11
If /home is on a separate partition, then choose to use it but NOT to format it.

If /home is part of / (root), then yes, that partition will have to be formatted during your new install.

---

### Post by Euphorion on 2009-07-11
Hallo Pen Sinner

> Do I delete the root or just format it over? Also, I dual boot with windows, so do I have to label that partition as /windows or something? I have sda1 as dell utility partition, sda2 as windows xp, sda3 as recovery, sda5 as intrepid ibex, sda6 as swap, and sda7 as /home. When I delete sda5, the swap becomes the new sda5 and /home becomes sda6. Will this delete or change any data in \home?There is no need to delete sda5 Intrepid if you are going to install Jaunty in this partition, just select format. The other partitions sda6 and especially sda7 your /home will remain where they are, in order to ensure that no data in /home is lost, just select to use sda7 without formating and as mount point /home. Here I assume that Jaunty will replace Intrepid, for I do not see any other Ubuntu partitions in your partition list.

There is no need to do anything with the windows Partition, when grub as boot manager is installed it will detect Windows and you will be able to select which operating system to boot via Grub.

But as in all cases when doing such a modification, I recommend that you backup your /home directory.

---

### Post by presence1960 on 2009-07-11
> **dryphi said:**
> I have the same question - will this install method delete the current contents of /home?

I'm trying an install today so I will let you know if I figure it out...

when you get to the Prepare disk space window of the install choose "manual" option. You really do not have to delete the root & swap partition. Highlight each one and set all pararmeters including ticking the format box for root (but not swap) This will format that partition. For root set mountpoint as /.  In the case of your separate /home partition highlight that and set mountpoint as /home. failure to do so will leave the data in that partition intact but it will not mount to your user directory as /home. it will be a data partition instead. **_Also for the /home DO NOT tick the format box or you will format that /home partition which means data will be wiped._**

---

