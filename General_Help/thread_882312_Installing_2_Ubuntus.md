---
title: "Installing 2 Ubuntus"
date: 2008-08-06
forum: General Help
---

### Post by Lovok on 2008-08-06
I have made weak attempts at researching this online, and I wonder if someone here has a link to a nice guide or something.

What I want to do is install Ubuntu two different times. One to have a stable working OS, and the other to fool around in and experiment.

This is how I have things partitioned :
Primary 1 : /
Primary 2 : swap (end)
Extended 3 :
[INDENT]/home
/usr
/opt
/tmp[/INDENT]
Primary 4 : empty

with 35 G unused space. It would be nice to also know how to share the /home partition. 

Thanks.

---

### Post by mb_webguy on 2008-08-06
First, write down which of your current partitions are which.  Running "sudo fdisk -l" should help.  When you install the second Ubuntu, choose to manually set the partitions.

Divide that 4th primary partition into your new root, /usr, /opt, and /tmp partitions (assuming you want to mirror your current partitioning scheme).  Select your current /home partition and label it accordingly, but DO NOT format the /home partition.  You should also be able to share your current swap partition between the two installations.  Once you're sure you have everything as you want it (and you're SURE you won't be formatting your /home partition), finish the installation.

When you boot up your new Ubuntu installation, you'll be using the same /home directory.

---

