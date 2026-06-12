---
title: "how update grub for all partitions"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2009-10-20
I have more then just one or two OS on my machine.

Let say 3 linux systems.

Ok they can be booted from the grub installed by last installation. So far OK.

Linux3 is having the one where the grub from mbr is pointing too.

I make update on Linux2, this has new kernel in it. This would normaly be written to the menu.lst, but it is now written to the menu lst on the linux2.

How do I propagate such changes also to the linux3 grub? 

Simple update-grub seems not to do this. Do I have to edit the menu.lst by hand? What to edit otherwise?

---

### Post by zvacet on 2009-10-20
> 

I make update on Linux2, this has new kernel in it. This would normaly be written to the menu.lst, but it is now written to the menu lst on the linux2.

Is new kernel default on menu.lst of your linux2?If it is I think it is O.k. because you boot from first linux and others are chain loaded.Maybe someone else give you better answer.

---

### Post by ottosykora on 2009-10-20
so far I realized that this is not the case. Booting goes allways from the last installed linux, I would call it linux3 in this case.

I did no manage to chainload newer linux from the first one. I tried, but all failed.

The only way I managed to run all inuxes was to install the grub from the linux3 to mbr and the list of the linux3 grub is now the one valid. But it does not reflect changes in the 'lower' linux, e.g. the linux2.

---

### Post by oldfred on 2009-10-20
Yes you have to manually edit the last install's menu.lst. The alternative of chainbooting works if you install each install's grub to each partition. That way you will get two menus regardless of how many operating systems you have the first has the chainboot entry to any number of other systems, the second is unique that that and is updated with kernel installs.

Look at the various reinstall grub commands for 
     "setup (hd[COLOR=DarkRed]x[/COLOR],[COLOR=Red]y[/COLOR])" (whatever your hard disk [COLOR=DarkRed]x[/COLOR] + partition #  [COLOR=Red]y[/COLOR] is)
                       to install GRUB to a  partition.

boot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

You do not have to have a separate grub partition but this helps explain chainbooting.
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

### Post by mosaic2s on 2009-10-21
> **oldfred said:**
> Yes you have to manually edit the last install's menu.lst. The alternative of chainbooting works if you install each install's grub to each partition. That way you will get two menus regardless of how many operating systems you have the first has the chainboot entry to any number of other systems, the second is unique that that and is updated with kernel installs.

Look at the various reinstall grub commands for 
     "setup (hd[COLOR=DarkRed]x[/COLOR],[COLOR=Red]y[/COLOR])" (whatever your hard disk [COLOR=DarkRed]x[/COLOR] + partition #  [COLOR=Red]y[/COLOR] is)
                       to install GRUB to a  partition.

boot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

You do not have to have a separate grub partition but this helps explain chainbooting.
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")

The last link showing the mapping for hard disks worked like magic. I am using ubuntu on first hard disk and other os on second. Am sharing the data folders for thunderbird and firefox. And now I can boot either ubuntu or other os thru grub on first hard disk.

thanks.

---

