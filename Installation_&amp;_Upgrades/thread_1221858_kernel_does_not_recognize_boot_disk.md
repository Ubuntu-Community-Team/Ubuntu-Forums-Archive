---
title: "kernel does not recognize boot disk"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by skrap on 2009-07-24
I have just upgraded to Jaunty and I am having some problems.  I have everything installed the way I want it but upon boot my system drops to built-in shell and then (initramfs)

Alert! /dev/disk/by-uuid/aa8ee64-4798-437a-a746-7a2663d6c95f does not exist. Dropping to shell
This only occurs with kernel 2.6.28-13
Everything works fine with kernel 2.6.28-11 but I have to manually switch to kernel -11

How can I get everything to boot automatically from kernel -13

Thanks for the help
amd 64 2gb RAM 2 hard drives separate /home

---

### Post by skrap on 2009-07-24
Hi again,  I could really use some help.  I think the fstab file that my kernel points to is wrong.  How do a get past the initramfs prompt

---

### Post by skrap on 2009-07-24
never mind. I just did a new install.

---

### Post by pbotros1234 on 2009-07-24
In the future, your problem was that line "/dev/disk/by-uuid/aa8ee64-4798-437a-a746-7a2663d6c95f does not exist".

That means some partitioning must have been done or something that changed your root partitions "UUID" -- its universal id number, basically. It couldn't find the partition with that UUID.

You could have simply changed your GRUB menu (/boot/grub/menu.lst) to say /dev/sdaX, where "X" is your root partition's number. This way the correct partition would be found.

---

### Post by skrap on 2009-07-25
Thank you for the reply.  That would have been much faster than a clean install.  Thankfully I have all of my data on a separate /home partition.
Next time I will know.

Thanks again.

---

