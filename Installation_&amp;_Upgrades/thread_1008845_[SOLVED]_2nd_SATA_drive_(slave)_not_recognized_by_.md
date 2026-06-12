---
title: "[SOLVED] 2nd SATA drive (slave) not recognized by Ubuntu"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by generic_idea_machine on 2008-12-11
Hi all, 

I just hooked up a 2nd HDD to the system that is not recognized by Ubuntu. The harddisk is picked up in the BIOS however. The HDD with the primary Ubuntu Partition is a SATA drive, however the second drive I am trying to install is a SATA2 drive.

 So far I have tried the following to get this working:
[LIST]
[*]Move the SATA cable from one port to another to see if this works
[*]enable AHCI in BIOS --> based on the instructions provided in the [following thread]("http://ubuntuforums.org/showthread.php?t=914515&highlight=sata+slave")
[*] Also if I plug the new SATA2 drive in the primary SATA port, then system does pick it up. However I need to add it as a slave. 
[/LIST]

I did some more research and got some conflicting information. Some post suggest it to be a driver support problem (lack of Seagate drivers) in Ubuntu...and to use "**Mint**" to get around this problem. Other post suggest it to be a problem with the ASUS mobo and with no apparent workaround, other than to be using the same kind of disks (brand, type and size) in order to get around this. I guess I forgot to state the obvious that I do have an [ASUS M2A-VM]("http://www.asus.com/products.aspx?modelmenu=1&model=1568&l1=3&l2=101&l3=496") mobo 


[Output of Lspci]("http://pastebin.com/m2821aade") 
[Output of lshw]("http://pastebin.com/m5139076a")
[messages file output]("http://pastebin.com/m6f72eeb7")

Am I missing something obvious?

---

### Post by generic_idea_machine on 2008-12-12
:guitar: **bump **:guitar:

---

### Post by Ifaistos on 2008-12-12
Have you tried using any other kind of distribution to check if it "picks it up".

You can use Knoppix Live CD, or even better parted magic.

If none of them "pick it up" then most prolly it's a Linux driver problem, or (most prolly) a wiring problem.

Hope that helps... let me know what happened...

---

### Post by bsmith1051 on 2008-12-12
Pastebin.com is cool, never saw that before!

Can you clarify which drive is the 1st and which is the 2nd (w probs)?  I see from your 'lshw' list that a Seagate 500 GB is being recognized as 'sda' (but with no partitions) and a Hitachi 250 GB is 'sdb' (with sdb1, sdb2, and sdb5 partitions).  Is the Seagate the drive you're having trouble with?  Is it suppposed to be a blank drive?

Have you tried using Partition Editor (aka gparted, available through Synaptic) ?  If the Seagate is a new drive and you just need to partition it, this is the easiest way.  You'll then need to manually add a reference to it in your /etc/fstab file, e.g. 
```
> sudo mkdir /data
> gksudo gedit /etc/fstab
```
then add a line such as:
```
/dev/sda1 /data ext3 relatime 0 2
```

---

### Post by pietjanjaap on 2008-12-12
Sata has no slave and master, they are alone on 1 cable.
Why do you need on the other cable?

Did you check the bios if your sata controller is enabled, and if the settings are correct, like raid, sata, ide etc.

Is your harddisk in fstab ?
Install "  gparted"  is a partion editor, to format your drive. Do you see your hd.
Install this "pysdm" storage device manager, to connect your hd to a map, do you see your harddisk.

---

### Post by generic_idea_machine on 2008-12-12
> **bsmith1051 said:**
> Pastebin.com is cool, never saw that before!

Can you clarify which drive is the 1st and which is the 2nd (w probs)?  I see from your 'lshw' list that a Seagate 500 GB is being recognized as 'sda' (but with no partitions) and a Hitachi 250 GB is 'sdb' (with sdb1, sdb2, and sdb5 partitions).  Is the Seagate the drive you're having trouble with?  Is it suppposed to be a blank drive?

Have you tried using Partition Editor (aka gparted, available through Synaptic) ?  If the Seagate is a new drive and you just need to partition it, this is the easiest way.  You'll then need to manually add a reference to it in your /etc/fstab file, e.g. 
```
> sudo mkdir /data
> gksudo gedit /etc/fstab
```
then add a line such as:
```
/dev/sda1 /data ext3 relatime 0 2
```

Thank you! It works!

The only thing I did differently was to mount the hard disk under the /media folder so it shows up under "Places" and on my Desktop. 

The only problem right now is that I have to sudo on a terminal to copy and delete files from the /media/hdd partition (newly added hard drive). What do I have to do in order to copy/past/delete files from Nautilus?

Many thanks once again for all your help. :KS

---

### Post by generic_idea_machine on 2008-12-12
> **generic_idea_machine said:**
> Thank you! It works!

The only thing I did differently was to mount the hard disk under the /media folder so it shows up under "Places" and on my Desktop. 

The only problem right now is that I have to sudo on a terminal to copy and delete files from the /media/hdd partition (newly added hard drive). What do I have to do in order to copy/past/delete files from Nautilus?

Many thanks once again for all your help. :KS

Think I was able to figure it out (permission issue for the actual mount point folder)

This fixed it :)
```
sudo chmod -R 2777 /media/hdd
```

---

