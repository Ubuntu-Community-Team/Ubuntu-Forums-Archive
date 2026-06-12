---
title: "Partition problem: Overwrite old Linux distro"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by btoone on 2005-11-14
During the partitioning part of the install I'm prompted with a few option concerning what to do with my disk (using the manual partition option).  I have a dual boot system and I want to replace my old linux distro.  The problem is that all the options seem to want to reformat my entire drive, rather than allow me to install on my existing linux partition.  Am I just misunderstanding what it is asking?  Or did I skip over the step that allows me to select the partition I want Ubuntu on?  Any help and or resources would greatly be appreciated.

---

### Post by ibanez88 on 2005-11-14
Ubuntu's partition tool is quite flexible.  You have the option of letting it blow off the whole disk, letting Ubuntu recommend settings for you, or manually editing the partition table yourself.  I've found that I like to use the guided partitioning to create one main ext3 filesystem and a seperate temp filesystem, and then resize it according to my needs..  Select the soon-to-be Ubuntu partition by highlighting it and hitting enter; then resize it if necessary, and follow the few steps.

You'll notice that it will NOT write the modified partition table unless you specifically move the cursor to the left and hit yes/ok at the final write warning.  Very user friendly compared to fdisk.

It definitely plays nicely with dual-boots, I have FreeBSD and am contemplating putting a third OS on (probably another Linux)..  However I have always managed my grub menu.list from Ubuntu by hand while correctly guessing the partitions for FreeBSD.  I am not sure if / how Ubuntu handles automatic integration of other OSes at the installation stage.

---

### Post by btoone on 2005-11-15
Thanks for the reply.  I figured out the problem.  In the partition help file it states that Ubuntu will not overwrite an existing linux distrobution.  Im going to remove that partition and then see if Ubuntu will let me set up new ones based on the available free space.

---

