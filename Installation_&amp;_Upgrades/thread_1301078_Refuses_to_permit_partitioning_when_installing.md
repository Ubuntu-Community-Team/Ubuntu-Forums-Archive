---
title: "Refuses to permit partitioning when installing"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by zozza on 2009-10-25
I am having installation problems and have tried the .iso files for 8.04-3 desktop and also 9.0.4-desktop.  

Everything seems to work with the installation until I get to the partition section.  There is the manual option which I select.

Then I see that I have four partitions:
/dev/sda1 - ntfs - XP - 82.8GB
/dev/sda2 - nfts - [no info[ - 61.3GB
/dev/sda3 - fat32 - NT/2000/XP - 4.9GB
/dev/sda4 - [no info] - [no info] - 47.1MB

I have no idea what sda3 and sda4 are.  Suggestions please?  

The option to create a new partition is greyed over.  All I can do is edit the partition which I rather suspect would be a bad idea.

So how can I split (create a new partition) in /sda2 since virtually all is free space?  

I cannot seem to get the options that the Ubuntu website says I should have (the ability to create a new partition).

Here (point 8) [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) it says you can drag the paritions (this is for 8.10 which I did not try) though I could not drag anything.  

Thanks.

---

### Post by earthpigg on 2009-10-25
sda3 and sda4 are probably partitions that your computer maker put on there for windows restore stuff.

is your intent to dual boot or just use ubuntu?

if just ubuntu: go ahead and delete all the partitions, and make new ones with whatever partitioning scheme you wish.

---

### Post by mick222 on 2009-10-25
when you get to partitioning select manual then selact th partition you want to change click on change partition or just change cant remember which.
resize partition and set to use this partition . hope that helps a little.Check this how to [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) Ubuntu can resize the partition itself you just tell it how bmuch you want for linux.

---

### Post by zozza on 2009-10-25
I want to dual-boot.

I have looked at the link above and made some comment below.

**Resizing Partitions Using the Ubuntu Installer**

  
**Automatic partitioning**

 
[LIST=1]
[*]Choose the First Option (It should be something like: "Resize IDE1 master, partition #1 (hda1) and use freed space"). 
[*]Specify the size of the new partition as a percentage of your entire hard disk. 
[*]Click on "Forward". 
[*]continue to [Finishing Ubuntu Installation]("https://help.ubuntu.com/community/WindowsDualBoot#head-6852d2e9b3e03d350a4271b58e3bdea4bbe81ad8") 
[*]
[/LIST]
 
[B]BUT I NEVER GET AN OPTION FOR AUTOMATIC PARTITIONING. 
[/B]

[B]
[/B]

**Manual partitioning**

 
[LIST=1]
[*]Choose "Manually edit partition table" 
[LIST]
[*]Listed will be your current partitions 
[/LIST]
[*]Select the partition you want to resize and press Enter. 
[*]Select "Size:", press Enter. 
[*]Select Yes, press Enter. 
[*]Type in a new size in Gigabytes for your partition, it's recommended you free up AT LEAST 10 GB of free space for your Ubuntu install. Press Enter when happy with your changes. It may take some time to apply the changes. 
[*]Create a swap partition of at least your amount of RAM (if you don't know, 2000 MB is a good value). 
[*]Create a partition for your Ubuntu installation, at least 10 GB. 
[*]Select "Finish partitioning and write changes to disk".
[/LIST]

I AM NOT SURE THIS IS WHAT I SEE WHEN I INSTALL.  AS I UNDERSTAND IT I TAKE A PARTITION LIKE /DEV/SDA2 WHICH HAS LOADS OF FREE SPACE AND SELECT 10GB AND THE TYPE IS EXT3 (YES?) THEN WITHIN THAT 10GB CHOOSE 2GB FOR SWAP?

I ALSO DO NOT UNDERSTAND WHY POINT 5. SAYS CHOOSE 10GB THEN 6. SAYS 2GB FOR THE SWAP AND THEN IN 7. ANOTHER PARITION OF 10GB?

DOES THAT SOUND OK?

THANKS AGAIN.

---

### Post by Mark Phelps on 2009-10-25
> **zozza said:**
> The option to create a new partition is greyed over.

That's because you have four PRIMARY partitions -- which is all you can have on one drive.  The partitioner won't let you create any more.

The most straightforward way to do what you want involves the following:
1) Copy the contents of the last partition to an external drive
2) Remove the last partition.
3) Create a new Extended partition to fill the unallocated space
4) Create a new NTFS partition in the Extended one -- large enough to hold the data you copied off
5) Create a new Ext3 (or Ext4) formatted Linux partition in the Extended one
6) Create a new Linux-swap partition in the Extended one.
7) Boot from the Ubuntu CD and choose Manual Partitioning and select the partitions you just created.

IF all goes well (Ubuntu installs and works OK), plug in the external drive and copy back the data to the new NTFS partition you just created.

---

### Post by zozza on 2009-10-26
Thanks.  Now I understand why my old laptop with two partitions allowed Ubuntu to suggest the resizing of a ntfs partition. 

Two points: first what XP based tool would you recommend for this partition business?  I have not done this before so would like something reputable. 

Second one of my ntfs drives is empty.  So presumably I can just convert it into a extended partition using the Ubuntu installer then add the extended partition and the swap partition as you suggested?

---

### Post by az on 2009-10-26
> **zozza said:**
> 
Two points: first what XP based tool would you recommend for this partition business?  I have not done this before so would like something reputable. 

I don't know of anything more reputable than Parted, the program that is used by every linux installer to do partitioning.  I would not suggest you use any XP partitioning tool.


> **zozza said:**
> 
Second one of my ntfs drives is empty.  So presumably I can just convert it into a extended partition using the Ubuntu installer then add the extended partition and the swap partition as you suggested?

Do you mean one of your NTFS partitions is empty?  Then yes, you can delete it and create an extended partition in the empty space.

---

### Post by zozza on 2009-10-26
My point is that I have not as yet installed Linux (hence these posts) so am not in it to use the tool.

Unless I can run it from the test mode or Live CD?  That's OK?

Thanks.

---

### Post by zozza on 2009-10-26
Would it not be easier just to deal with deleting the ntfs partition then creating the extended partion then adding the extended partion and awap partition (within the new extended partion) during the Ubuntu installation process?

---

### Post by zozza on 2009-10-26
Ignore me....I realise that Partition is the installation tool.

---

### Post by Bartender on 2009-10-26
zozza -
Your confusion is certainly understandable.  
- You see a partitioning tool when you're trying to install using a LiveCD or alternate install CD.
- You also can access the partitioning tool if you just boot into the LiveCD desktop, then go into System>Gnome Partitioner (or whatever it is they call it right now).
- Once you have Ubuntu installed, you can download and install the Gnome Partitioner and it will show up in System.
- You can download GParted LiveCD (link under my sig)

Although they're all based on gparted, the first partitioner described above doesn't look like the other three.  The other three look the same but they don't act the same due to mounted partitions.  

It doesn't make any sense until you understand what each one will and won't do (or will do with a tweak or two...)

+1 on previous responses suggesting wiping the ntfs partition, creating an extended partition out of the space.  Then create logical partitions for Ubuntu manually or just let it install to the space.

---

### Post by Mark Phelps on 2009-10-26
> **zozza said:**
> Second one of my ntfs drives is empty.  So presumably I can just convert it into a extended partition using the Ubuntu installer then add the extended partition and the swap partition as you suggested?

NO -- AFAIK, you can only have ONE Extended partition per physical drive.  So, if convert one partition already there, you will have to remove any others you want inside it and recreated them inside it.

---

### Post by raymondh on 2009-10-26
4 primary partitions or ..... 3 primary partitions + 1 extended

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

