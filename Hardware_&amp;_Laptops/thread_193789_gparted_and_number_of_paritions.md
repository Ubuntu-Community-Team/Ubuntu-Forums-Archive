---
title: "gparted and number of paritions"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by spyke01 on 2006-06-10
i just installed gparted because i want to create a partition strictly for music(so i can add and delete them via window$ and nix) but it wont allow me to resize my ntfs partition and create another one. 

im not sure if im allowed to have more than 4 partitions, heres my fdisk
> 
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16843   135291366    7  HPFS/NTFS
/dev/hda2           16844       19346    20105347+  83  Linux
/dev/hda3           19347       19457      891607+   5  Extended
/dev/hda5           19347       19457      891576   82  Linux swap / Solaris


is there some way that i get one more partition on this drive?

---

### Post by tonyr on 2006-06-10
Generally, you may have 4 **primary partitions**, or 3 **primary** and 
1 **extended** partition.  The **extended** partition may be further 
subdivided in to many **logical** partitions.  Your partition table shows
2 **primary** partitions, **/dev/hda1** and **/dev/hda2**,
1 **extended** partition, **/dev/hda3**, and 1 **logical** partition, **/dev/hda5**,
inside the **extended** partition.  You should be able to resize (shrink) the
NTFS partition, although you may have to do it from the Windows side, and add 
another **primary** partition in the freed space.

Your current partition arrangement is rather awkward.  It would be more work, and a little bit
more risky, to rearrange your partitioning completely, but it can be done.  It would be more
reasonable to have this arrangement:
/dev/hda1  primary NTFS 
/dev/hda2  primary Linux ext3
/dev/hda3  primary reserved
/dev/hda4  extended
/dev/hda5  logical(inside extended) swap
/dev/hda6  logical(inside extended) data FAT32 or ext3

[This]("http://users.bigpond.net.au/hermanzone/p3.htm") document has some good information on partitioning.    [This]("http://www.psychocats.net/ubuntu/partitioning.html") one does, too.

There are several threads that discuss partitioning problems and solutions. Search on
**partitioning** in the **Search** box on this page, or under the **Advanced Search**
entry in the **Search** drop down menu.

---

### Post by spyke01 on 2006-06-10
ok restarted and booted live cd, launched gparted, resized, pressed apply and now im screweed

[http://ubuntuforums.org/gallery/showimage.php?i=2839&original=1&c=2](http://ubuntuforums.org/gallery/showimage.php?i=2839&original=1&c=2)

tried a restart, cant boot into xp

---

### Post by tonyr on 2006-06-10
Have a look at this
[http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm") 
and see if any of that looks familiar.

What happens when you try to boot Windows?

---

### Post by spyke01 on 2006-06-10
tells me theres nothing there to boot, gparted picks up that the ntfs was to be resized and a fat32 added, but it shows both of them as unknown, im trying to get testdisk to fix it but it doesnt want to fx it im hoping that i dont have to format, too much data will be lost

---

### Post by tonyr on 2006-06-10
If you didn't format the new partition, you may be able to simply restore the partition
definition of the NTFS partition to what it was originally.

---

### Post by spyke01 on 2006-06-10
nope didnt format, how do i do restore the definition(the ntfs partition was the only one i touched)? gparted will only give me the option to delete or format

---

### Post by tonyr on 2006-06-10
The general procedure is to delete the new partition that you created, and extend the
NTFS partion to cover all of the released space.  Gparted should be able to do that.
You can also install **qtparted** another tool like **gparted** (some like it better),
or use **fdisk**, a command line tool.  **fdisk** offers more detailed control,
but requires that you be more familiar with disk drive details.

---

### Post by spyke01 on 2006-06-11
thanks tonyr, ill try this tommorow, and let you know, thanks for all the help so far

---

### Post by spyke01 on 2006-06-11
oh crap it looks like im screwed, finally able to make the partition, looks like it was the swap partition that screwed me in the first place(i thought they were all unmounted but swap was enabled). If theres anything you can suggest itd be great, finally got testdisk working and it says that im screwed(shows no data for that partition and that the boot sector fo it is fine)

---

### Post by tonyr on 2006-06-11
It's hard to imagine why the swap partition would cause any problems. Show
some more information.  What does **fdisk -l /dev/hda** show now (or gparted)?

What is your **testdisk**.  Do you mean the liveCD?

---

### Post by spyke01 on 2006-06-11
testdeisk is a partition recovory program, i finally said forget it and wiped it and put on a year old backup i had

---

