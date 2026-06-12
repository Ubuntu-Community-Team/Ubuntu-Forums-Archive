---
title: "Installation Partitioning Problem"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by pkaplan on 2006-02-02
I am trying to install kubuntu onto a machine with an existing linux installation.  I want to dual boot.  When I get to the partitioning section, the installer doesn't show any of the existing partitions, offering me instead only the possibility to automatically select and reformat the entire disk or manually enter all partition info.  Other distros detect existing partitions and let you select which ones to use for your  installation.

My disk:
/dev/hda1  reiserfs  10G existing /
/dev/hda5  swap        1G existing swap
/dev/hda6  reiserfs  20G existing /home
/dev/hda7  reiserfs  10G existing /home/data
/dev/hda3  reiserfs  10G proposed kubuntu /
/dev/hda4  reiserfs   20G proposed kubuntu /home
/dev/hda8  swap        1G proposed kubuntu swap

What's the problem?  How can I install kubuntu into hda3&4?
TIA
Paul

---

### Post by deBaas on 2006-02-02
[QUOTE=pkaplan]I am trying to install kubuntu onto a machine with an existing linux installation.  I want to dual boot.  When I get to the partitioning section, the installer doesn't show any of the existing partitions, offering me instead only the possibility to automatically select and reformat the entire disk or manually enter all partition info.  Other distros detect existing partitions and let you select which ones to use for your  installation.

My disk:
/dev/hda1  reiserfs  10G existing /
/dev/hda5  swap        1G existing swap
/dev/hda6  reiserfs  20G existing /home
/dev/hda7  reiserfs  10G existing /home/data
/dev/hda3  reiserfs  10G proposed kubuntu /
/dev/hda4  reiserfs   20G proposed kubuntu /home
/dev/hda8  swap        1G proposed kubuntu swap

What's the problem?  How can I install kubuntu into hda3&4?
TIA
Paul[/QUOTE]
Just read the installer. Or you ereae your whole disk, or you assigh the larges part of free disk space to de assigned automaticaly or you edit the lay out manualy. This last option will bring up your existing partitions and free space. It's not that hard.

---

### Post by Herman on 2006-02-02
Would it be the same (or similar) problem to the one meono solved in [this thread]("http://www.ubuntuforums.org/showthread.php?t=124554")?

---

### Post by pkaplan on 2006-02-03
Herman,
The description of the problem is the same.

After I select "Manually edit parition table" from the "(!) Partition disks" screen,
I get a screen showing "IDE1 master (hda) - 80.0 GB" and no partitions shown below.  The following screens never show evidence that the kubuntu installer sees the existing partitions

The disk was partitioned with Mandriva's partitioning tool (diskdrake).  I thought this was based on QTparted, but neither QTparted or Gparted is on my system.  I've used diskdrake to successfully parition 3 prior disks including two that already contained NTFS partitions.

Perhaps this output will tell you something I don't see:

device        Type        Size(G)   Start sector  Total sectors       Cylinders
/dev/hda1  reiserfs   10                      63          20986497               0 -  1387
/dev/hda5  swap        1           20986623            2101617         1388 -  1526
/dev/hda6  reiserfs   20          23088303          41957937         1527 -  4301
/dev/hda7  reiserfs    9.8        65046303          20563137         4302 -  5661
/dev/hda3  reiserfs    9.7        85609440          20472480         5602 -  7015
/dev/hda4  reiserfs  19         106081920          40944960         7016 -  9723
/dev/hda8  swap       0.996    147026943          2041137         9724 -  9858
Empty                        3.4       149068080           7227360         9859 - 10336

Paul

---

### Post by Herman on 2006-02-03
I don't know, this problem a little too advanced for me, I'm interested in learning about it, but I don't know enough at this stage to be able to help. Maybe someone more experienced wil come along. :confused: (Herman)

---

### Post by lha on 2006-02-03
[QUOTE=pkaplan]Herman,
The description of the problem is the same.

After I select "Manually edit parition table" from the "(!) Partition disks" screen,
I get a screen showing "IDE1 master (hda) - 80.0 GB" and no partitions shown below.  The following screens never show evidence that the kubuntu installer sees the existing partitions

The disk was partitioned with Mandriva's partitioning tool (diskdrake).  I thought this was based on QTparted, but neither QTparted or Gparted is on my system.  I've used diskdrake to successfully parition 3 prior disks including two that already contained NTFS partitions.

Perhaps this output will tell you something I don't see:

device        Type        Size(G)   Start sector  Total sectors       Cylinders
/dev/hda1  reiserfs   10                      63          20986497               0 -  1387
/dev/hda5  swap        1           20986623            2101617         1388 -  1526
/dev/hda6  reiserfs   20          23088303          41957937         1527 -  4301
/dev/hda7  reiserfs    9.8        65046303          20563137         4302 -  5661
/dev/hda3  reiserfs    9.7        85609440          20472480         5602 -  7015
/dev/hda4  reiserfs  19         106081920          40944960         7016 -  9723
/dev/hda8  swap       0.996    147026943          2041137         9724 -  9858
Empty                        3.4       149068080           7227360         9859 - 10336

Paul[/QUOTE]

Take careful look at cylinders used by hda7 and hda3. Hda7 uses 4302-5661 and hda3 uses 5602-7015, so these partitions overlap at cylinders 5602-5661! This will surely lead to loss of data if you don't fix this. You may have lost some data already. No wonder partitioner didn't understand your partitions...

Meono was able to solve his/her problems by deleting one of the partitions that were overlapping. Well, I just remembered I had a similar problem once, too. Fortunately, I didn't have any valuable data on either of my overlapping partitions, I was able to remove them both. (In matter of fact, I reformatted the whole drive as I was upgrading my hds.)

---

### Post by Herman on 2006-02-03
Thank You Iha, I'm impressed, (and a little bit wiser), thanks again,:-D  (Herman)

---

### Post by pkaplan on 2006-02-03
My mistake on the cylinder info (I had to copy the info manually since diskdrake doesn't generate such a table).

Actually there are no overlapping cylinders, so I'm still stuck with apparently clean partition information and a kubuntu installer that doesn't seem to believe there are any partitions on the disk.

Really want to get kubuntu to /dev/hda3&4

---

### Post by pkaplan on 2006-02-04
I ended up deleting /hda3,4&8 and now the installer sees my existing partitions.  I wonder whether it had to do with the order I created the partitions on the disk?  i.e., 1,5,6,7,3,4,8.  After letting the installer go it wound up as 1,5,6,7,8,9,3.
On to other install problems
Paul

---

### Post by lha on 2006-02-04
[QUOTE=pkaplan]I ended up deleting /hda3,4&8 and now the installer sees my existing partitions.  I wonder whether it had to do with the order I created the partitions on the disk?  i.e., 1,5,6,7,3,4,8.  After letting the installer go it wound up as 1,5,6,7,8,9,3.
On to other install problems
Paul[/QUOTE]

You are right on that one. How could I miss that?! One of your logical partitions (hda8) was outside the extended partition. I have never seen that happen. Usually the order of partitions doesn't matter with Linux, but a logical partition outside of extended partition - that's a really weird situation. Glad to hear you found the solution.

---

