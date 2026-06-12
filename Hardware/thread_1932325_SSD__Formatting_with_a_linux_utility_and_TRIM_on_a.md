---
title: "SSD : Formatting with a linux utility and TRIM on an AMD motherboard"
date: 2012-02-27
forum: Hardware
---

### Post by Lagori on 2012-02-27
Hello,
 
I don't know if it's the right section to ask those questions, I thought it would be the most appropriate one since it concerns SSDs. Sorry if I was wrong.

My normal setup on my PC is a dual boot Windows 7/Ubuntu installed on a hard drive.

Sometimes I need to reinstall one of my OS, when it happens I format the partition with a linux utility such as GParted before beginning the installation process.
 
Recently I bought an SSD.

In the past there was a problem with such a device : when you would delete a file at the OS level, the controller of the SSD was not immediately aware of it. If you wrote a lot of data that you erased afterwards, after a while the controller was full of invalid data even though the file system seemed to still have a lot of free space.
And yet the controller needs free space for some of its internal tasks such as wear leveling and garbage collection.
Luckily manufacturers build all their SSDs with some space which is neither available to the user nor to the OS nor to any utility. This space usually corresponds to 7% of the user accessible space and enables the controller to always have some space for its internal tasks no matter how the SSD is used. It's called over-provisioning.

7% is good but more is better, that's why it's sometimes advised not to format all the available space on the SSD and let some unallocated space. This space will be used by the controller as over-provisioning and added to the pre-existent 7%. It will help reduce the write amplification (the controller will write less onto the NAND) and thus the SSD will maintain good performance over time.

Now going back to the first models of SSDs, if you didn't do that, if you would format all the available space, at the beginning the controller could use the original 7% plus all the free space at the OS level. However if the user wrote a lot of data and deleted it afterwards after a while the controller could only rely on the first 7% for its internal tasks because NAND was full of invalid data and the controller had no means to distinguish between valid data and stale data.
Besides each time the user wanted to write a new file, even a small one like 4KB for example, the controller had to overwrite stale data and you had to pay a performance penalty because the controller had to read a whole block of maybe 512KB to load it into the DRAM chip, modify the portion of data that changed and rewrite the whole block onto the NAND (read-modify-write cycle).

These 2 things were the reason why the performance on the first SSDs would degrade over time.

That's why manufacturers implemented TRIM. Basically TRIM is supposed to tell the controller, each time you erase a file at the OS level, to delete the LBA addresses corresponding to this file in its allocation table, then afterwards at one point in time garbage collection will erase the data on the NAND. Thus, provided that the user let some free space in his file system (10% to 20%) the controller will always have enough over-provisioning and the user will never have to pay the read-modify-write cyle penalty because there will be always some free space on the NAND.

I'm not sure that all of this is 100% correct, it's just what I understood after reading [the]("http://www.anandtech.com/show/2614") [trilogy]("http://www.anandtech.com/show/2738") [of]("http://www.anandtech.com/show/2829") articles about SSDs written by Anand Lal Shimpi. So feel free to correct me.
 
So TRIM is an important command for an SSD because without it performance goes down.
 
I think that for the TRIM command to be passed to an SSD 4 things need to support it : the file system, the OS, the SSD and the SATA controller driver.

I mainly use ext4 and ntfs as file systems which support TRIM, my Operating Systems are Windows 7 and Ubuntu which support TRIM (TRIM support was added to the linux kernel in version 2.6.33) and [my SSD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820167053") support TRIM.

However concerning the SATA controller driver I'm completely at a loss.
I've got an [AMD motherboard]("http://www.asus.com/Motherboards/AMD_AM3/M4A78LTM_LE/"), so here is my first question :

**Is there any linux driver for my mobo that supports TRIM (be it proprietary or open-source) ?**
(For Intel motherboards I know it's the case but AMD... even after looking on Google I'm still not sure.)

I've got a second question.
 
I think that if you format a partition with the formatting tool from Windows 7 then TRIM command is sent to the SSD. On the contrary if you delete a partition with the same tool TRIM command is not sent :
 
 > [INDENT]TRIM is triggered by two things it seems. Either deleting a file and emptying the recycle bin (to truly delete it) or formatting the drive. Simply deleting a partition doesn't TRIM the entire drive as I found out the hard way.[/INDENT][source]("http://www.anandtech.com/show/2829/15")

But what happens if you use GParted live-cd ?

I've read that for Linux to pass the TRIM command to an SSD you have to add the 'discard' option in /etc/fstab

But if I use a GParted live-cd and open a terminal to see what contains /etc/fstab there's no information about the partitions I'm going to format.
Do I have to add a line ([Device] [Mount Point] [File System Type] [Options] [Dump] [Pass]) for each partition I'm about to format ?

If so will the changes be taken into account immediately, don't you need to reboot (and thus lose the changes made in /etc/fstab since it's a live-cd) ?

In other words **if I format an ext4 partition with GParted live-cd will it send the TRIM command to my SSD ?**
Same question if I format a ntfs partition ?
If I delete a partition ?
And finally if I delete the whole partition table in case I'm going to be starting over from scratch?
 
Any help and advice on these 2 problems would be greatly appreciated.
Thank you in advance.

PS : sorry if my English was bad, it's not my native language.

---

### Post by oldfred on 2012-02-27
Welcome to the forums.

I am not sure I can answer your exact questions. But will try to add to the confusion. I recently bought a SSD just to boot Ubuntu.

When using gparted to partition (and optionally format) you do not have partition mounted. I do not then think discard applies as you are not writing data to the partition, just setting it up. No entries are in an fstab until you install a system can format the partitions.

If you are just using SSD for Linux gpt is a newer prefered partitioning scheme over the 30 year old MBR. But Windows requires MBR unless booting with the new UEFI systems.

Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

Basically you want a non-journalized system, either ext2 or ext4 with journal turned off and the noatime, discard options in fstab.
On a hard drive you want a journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There’s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.

---

### Post by Lagori on 2012-02-27
Thank you very much for your answer.

> **oldfred said:**
> 
When using gparted to partition (and optionally format) you do not have  partition mounted. I do not then think discard applies as you are not  writing data to the partition, just setting it up. No entries are in an  fstab until you install a system can format the partitions.


Here's what I believe :

TRIM is needed to tell the controller which data are invalid :

> In [computing]("http://en.wikipedia.org/wiki/Computing"), a **TRIM** command allows an [operating system]("http://en.wikipedia.org/wiki/Operating_system") to inform a [solid-state drive]("http://en.wikipedia.org/wiki/Solid-state_drive") (SSD) which blocks of data are no longer considered in use and can be wiped internally.[source]("http://en.wikipedia.org/wiki/TRIM")

So TRIM is needed every time I delete something in my file system.

When I format a partition on which there's already an OS installed, all the files on the partition are deleted from the file system. So I need to tell the controller that all of these data are no longer valid, which is the purpose of TRIM.

In other words when I format a partition I need the TRIM command to be sent to the controller. To prove this here's what Anand wrote on [this page]("http://www.anandtech.com/show/2829/10") :

> In the Anthology I simulated this worst used case by first filling the  drive with data, deleting the partition, then installing the OS and  running my benchmarks.  This worked very well because it filled every  single flash block with data. [...]
The problem here is that if a drive properly supports TRIM, the act of  formatting the drive will erase all of the wonderful used data I  purposefully filled the drive with.  My &#8220;used&#8221; case on a drive supporting TRIM will now just be like testing a drive in a brand new state. He explains that in order to simulate a used SSD with poor performance, before TRIM was implemented he would simply fill an SSD with data, then format the partition in order to install an OS. The act of formatting didn't erase any data on the NAND at that time and the controller would still think that all of the data were still valid leading to poor performance.

However since TRIM he couldn't do that anymore because when formatting the partition, the data were effectively erased from NAND not only from the file system.

This is what I want : when I format a partition I want the data to be erased from NAND or the TRIM command to be sent to the SSD so that the controller knows that all the data are no longer valid.

However I don't think Anand used GParted when he made his tests, he probably used the formatting tool in Windows.

So I know Windows formatting tool does send the TRIM command but I don't know about GParted or any other Linux formatting utility.

What I know is that with Linux the TRIM command needs the 'discard' option but this option can only be used on a mounted partition and GParted doesn't format a mounted partition.

So my guess is that every time I want to format a partition full of data I've got 2 choices :

1) format the partition in ntfs or fat with Windows in order to be sure that the controller knows that all the data must be considered as invalid, then format the partition in ext4 with GParted.

2) make a [secure erase]("http://blog.ocztechnology.com/?p=367") which is a little overkill.

I would like to know if there's anyone here who used GParted or any other Linux utility to format a recent SSD full of data (when I say 'full of data' I mean almost all the SSD not just a small partition), did they notice that the performance were back as if the SSD was brand new or not ?

---

### Post by fjgaude on 2012-02-27
I'll be doing what you wish, using gparted to format a used SSD when Ubuntu 12.04 is released in late April. I using the SSD as boot with the Alpha version now and will start again with a clean drive then.

I presently use "fstrim /" daily to keep the boot drive healthy. I only use "disk utility" to test the read speed of the drive. The speed is in the range of 450MB/sec now. It never was any better than 520. It's been in the 450 range since about a week after I started using it. I've had it for several months now without issue. Gosh, the system is quick and fast.

I believe any drive with the latest Sandforce controller works fine in Linux, with or without the "discard" item in the boot line. The SATA controller has nothing to do with the issues you are concerned about.

I wish I had a better way to test read speed!

---

