---
title: "How do I activate booting to an existing partition without re-install?"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by PatrikG on 2009-04-18
Hi everyone,

I'm a newbie to Ubuntu but I'm really starting to like it so I hope someone can help me out.

Short description of the problem:
- HDD previously used in a dual boot system
- Ubuntu installed on it's own partition
- New computer with only one HDD
- How do I get Ubuntu to boot from the previously installed partition?
- Re-install not a first option

Background:

I used to have a WinXP-only computer, and to try out Ubuntu I installed it on a second harddrive (SATA). I made one partition for Ubuntu and one for music/pictures/etc. Then using GRUB I could switch between XP and Ubuntu. so far no problems.

Problem:
But now I have taken the second harddrive out of the old computer, and put it together with a D945GCL2F motherboard, hoping that it would just boot into Ubuntu, but no such luck...

I have tried using the partition manager and set the partition to "boot" -> no luck. At least it doesn't say that NTLDR is not found anymore.

I (think) I have gotten GRUB installed by doing:

sudo grub
root (hd0,4) (this is the partition where I have the Ubuntu install)
setup (hd0)

The output after the setup says that everything is ok and installed. but it still won't boot. I don't even get a screen saying that GRUB has started, only a one liner about inserting a boot disc.

To re-install is my last resort only due the amount of data I have lying on the other partition, and I only get the option to reformat the entire drive, not to install it to a specific partition, or is that possible?

So, does anyone knows how I can get Ubuntu to boot up from an existing installation?

Feel free to ask if any more information is needed.

---

### Post by pbpersson on 2009-04-18
1.  Verify the hard drive is included in the boot order in the BIOS
2.  Boot from Live CD, mount the partition, and check the /boot/grub/menu.lst file to verify everything looks good
3.  Double-check your partition numbering, I know it can be a little confusing.  Is (hd0,4) the same as saying sda5?

It sounds like you are on the right track

---

### Post by Mark Phelps on 2009-04-18
Start by running "fdisk -lu" (that's a lowercase L, not a one) in a terminal.  That will display a list of drives and partitions.

---

### Post by PatrikG on 2009-04-19
Ok, I haven't rebooted yet, but just to check I'm posting all info that I can get.

Running fdisk:
root@ubuntu:/# sudo fdisk -lu
sudo: unable to resolve host ubuntu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000eb978

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   465981389   232990663+   7  HPFS/NTFS
/dev/sda2       465981390   488392064    11205337+   5  Extended
/dev/sda5   *   465981453   487347839    10683193+  83  Linux
/dev/sda6       487347903   488392064      522081   82  Linux swap / Solaris

And checking the partitions in grub gives this (may be there is a better way than autocomplete...):

grub> root (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x82

and find gives this:
grub> find /boot/grub/stage1
 (hd0,4)

And I have done the setup in Grub (setup (hd0,4) ) and it said success.

I also followed the steps here: 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

So, fingers crossed, I'm rebooting again...

---

### Post by PatrikG on 2009-04-19
Solved! :D

To help out others with the same problem, this is what I did: look at the partition table, it says "Extended" on sda2, and I've put the boot flag on sda5. 

I used the partition manager to set the boot flag to sda2 instead, and there GRUB was, in all it's black-and-white glory!

Then of course, all the steps I have done before where probably necessary as well... ;)

Hope this helps other with similar problems!

---

### Post by jcoles on 2009-04-22
How did you get grub to list the possible partitions? 
How did you determine the correct disk,partition value (hd0,4)? fdisk lists only the standard device names. 
My SATA drive is /dev/sdc. I tried setup (hd2,0), but I only get "Error 12: Invalid device requested". Guessing at other values is dangerous. I need to be completely sure that I am specifying the correct drive.

If I remove a drive, will that wreck everything because the device name might change from /dev/sdc to /dev/sdb or something?

grub is not well explained anywhere.

Thanks.

---

### Post by jcoles on 2009-04-23
OK. I figured out that I need to enter
root (hd2,0)
setup (hd2,0)

I am doing this on a Linux partition copied from /dev/sda1. Now I can boot from the SATA drive (/dev/sdc), but the original /dev/sda1 partition is still the one that is used. I think I need to run updgate-grub on the new partition. But how? update-grub takes no drive parameter. It always works on the current partition.

---

### Post by jcoles on 2009-04-23
Turning off the original drive in the BIOS and booting from the new drive, the system hangs at "Loading..". 
I copied the files, not the partition, from the original drive, which is still in the machine. I wanted to copy my system files to a new partition on the new drive (/dev/sdc) and boot from the new partition. Is this actually possible? Or is a re-install plus a long re-fetching of months of updates the only way I can do this?

I see that the copied menu.lst contained the UUID of the old drive and changed to using the device name instead. There is also another inactive drive at /dev/sdb. Do drive names change as HDDs are added and removed? I have tried hd0,0 hd1,0 and hd2,0. grub find has never listed hd2,0 but lists hd0,0 and hd1,0 when both sda and sdc drives are enabled.

It is all very confusing and hard to troubleshoot.

---

### Post by jcoles on 2009-04-24
I solved the problem by using gparted to copy the entire Linux partition from the old drive to the new drive. All I had to do then was set the boot flag. I didn't need to edit menu.lst as the new drive becomes /dev/sda when the old drive is no longer connected.

---

