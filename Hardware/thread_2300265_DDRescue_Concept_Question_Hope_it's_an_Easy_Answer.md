---
title: "DDRescue Concept Question: Hope it's an Easy Answer!"
date: 2015-10-24
forum: Hardware
---

### Post by CanadianPilgrim on 2015-10-24
I am a novice with linux. I hope I am in the right forum for answers because finding the right forum has proved as difficult as finding an answer to what should be a simple question.

I used ddrescue to clone a failing hard drive (via USB) direct to another disk (not to an image file). ddrescue informed that it encountered 8 read errors for a total errsize of less than 1MB. The destination drive, which was new and had been formatted NTFS, is now reporting in diskmgmt (Windows) that the destination disk is RAW.

The description of ddrescue's operation is as a 'raw imaging tool' therefore, I assume, the destination drive is supposed to be RAW. If so, this is where I am stuck in concept. What I am supposed to do with the new drive now? I have searched for hours and cannot find an answer to these two simple questions: 

1) is a ddrescue disk-to-disk clone operation supposed to render a RAW destination disk? 
2) If yes to #1, then how do I deal with it to turn it into an operational NTFS OS disk (as a clone of the original)?

If I am in the wrong place for answer, please suggest where I may go if you have an idea. I am getting rather desperate. I have been working on a disk rescue for 3 weeks and have a pending RMA return on the failed drive of 30 day to post it!

---

### Post by TheFu on 2015-10-24
ddrescue is a bit-for-bit copy tool that handles disk errors nicer than the original dd tool. It is dumb and assumes the program user knows when, where, and how to make the copies.

So...  if you'd like more detailed help, please post each of the following, being very clear about the requested details:
a) the exact **ddrescue** command used
b) the output,  using [code tags]("http://blog.jdpfu.com/code_tags"), of **sudo parted -l** for the source disk.
c) the output,  using [code tags]("http://blog.jdpfu.com/code_tags"), of **sudo parted -l** for the target disk.

---

### Post by CanadianPilgrim on 2015-10-24
I was asking for a theoretical answer which, I presume from your response, would be "no, ddrescue is not supposed to render a RAW result in the destination drive". Here is a picture of the commands used and the output results (screenshot). 

[https://scontent-sea1-1.xx.fbcdn.net/hphotos-xpf1/v/t1.0-9/10984146_1646510985602920_8575644193415692954_n.jpg?oh=e8337afe3d21b6fdeb5e9f7129395887&oe=56B7E823](https://scontent-sea1-1.xx.fbcdn.net/hphotos-xpf1/v/t1.0-9/10984146_1646510985602920_8575644193415692954_n.jpg?oh=e8337afe3d21b6fdeb5e9f7129395887&oe=56B7E823)

---

### Post by TheFu on 2015-10-24
You shouldn't copy a drive device to a partition. It needs to be either  drive-->drive  or partition-->partition.

---

### Post by CanadianPilgrim on 2015-10-24
Thank you Fu. So, then the answer to my 1st question is that ddrescue is NOT supposed to render a RAW result? What I should get is a clone of the source without any further adjustments to the file records or disk structure?

---

### Post by J_Me on 2015-10-25
The thing is your copying over the partition tables of sdc with it's mount points and all to a existing partition on sda. Try wrapping the output to a image (/dev/sda2/theSDCdisk.img) and then manually mount it. > Thank you Fu. So, then the answer to my 1st question is that ddrescue is NOT supposed to render a RAW result? What I should get is a clone of the source without any further adjustments to the file records or disk structure?ddrescue does what you tell it to do, I think that's why dd also goes by the name disc destroyer.

---

### Post by The Cog on 2015-10-25
As others have pointed out, you copied the entire disk sdc to a partition (partition 2) of another disk (sda).
I don't think anything will be able to easily read that partition now. Assuming your failing disk is still readable, it would probably be best to have another go at making a copy.

However, you need to be clear what you are trying to do, and I can't work it out from what you posted. You say you copied the failing drive to a new drive but the picture shows that's not the case. If sda was the new drive, then I would not expect there to be a partition already on it (it seems that sda1 already existed). Before you have another go, please explain on more detail what you are trying to do and make sure people here agree.

What worries me is that perhaps you are confusing drives with partitions. A hard drive has a bootsector and partition table at the start, followed by a number of partitions each of which is formatted with a filesystem such as NTFS. The partition table describes where on the disk each partition starts and ends.  More confusing perhaps is that floppy disks are formatted directly without a partition table and with the filesystem starting at the beginning of the disk (after a leading bootsector). Maybe that's why Microsoft decided to call hard drive partitions "drive"s. With DOS, A: and B: were floppy disks, and C: was the first partition on the hard drive. Hard drives and partitions are not interchangeable. I suspect that you tried to copy the failing drive in its entirety and including the partition table to a partition on your existing windows hard drive, perhaps trying to call it D:. I hope you can see now why that wouldn't work.

It is possible to copy an entire drive to a new drive, and this does work, even down to windows booting properly. It is possible to upgrade the hard drive size on a machine this way - I've done it. But of course I mean a complete new hard drive here. From a shop.

It is possible that you could copy the contents of you failing drive to a partition on an existing hard drive if that's what you are trying to do. This would involve making sure the recipient partition was large enough to accept the rescued partition, and of course copying the contents of the correct partition across. But the failing disk may have more than one partition. 

It would be a good idea to explain exactly what you are trying to do, i.e. copy partition contents or copy an entire hard disk, and post the output of the command "parted -l" with both disks connected so we can see what is on each disk. Then we should be able to advise what the proper command is to make the required copy.

P.S. I googled it, and it seems that RAW simply means that windows can't identify the filesystem type. I would expect exactly that if windows was looking at a partition table and trying to use it as FAT or NTFS filesystem.

---

### Post by TheFu on 2015-10-25
If all the questions I'd asked originally had had been answered, then we wouldn't be guessing so much.
OP - throw us a bone, please.

I cannot answer what windows should or should not be capable of.  Stopped caring around 2008.

---

### Post by CanadianPilgrim on 2015-10-25
Thanks for all the assistance. It appears the answer was simple. I cannot copy a drive with partitions to a partition on a new drive. This rule was not published anywhere I looked when I studied for this. Following this rule, the new drive is now up and running.

The destination drive was a "new" 500GB HDD. I separated it into 2 partitions because the failing drive was a 240GB SSD with only about 100GB used. The destination drive is 500GB HDD and I wanted not only to preserve some of this drive for second run at ddrescue, if needed, but I was using the 500GB HDD as a guinea pig because ultimately I want to clone either the failing drive or a clone of it to another smaller SSD and I read that is more difficult to do from a cloned drive if the drive is large though the space is empty.

Assuming now I will make my final clone from the new 500GB HDD that should have 3 partitions from the failing drive (see attached image), and my destination drive is a 120GB SSD, any recommendations on what tool to use to do it (the 500GB HDD does not need to be rescued so I don't think ddrescue is the right tool)? Would I clone over partition by partition?[IMG]https://www.facebook.com/digmytech/photos/p.1646691555584863/1646691555584863/?type=3&permPage=1[/IMG]

---

### Post by CanadianPilgrim on 2015-10-25
In case the image link above is not working. [https://scontent-sea1-1.xx.fbcdn.net/hphotos-xfa1/v/t1.0-9/10302374_1646692575584761_1834228059568532121_n.png?oh=28a814fcd2c503b3e55040f852493ace&oe=56BCC378](https://scontent-sea1-1.xx.fbcdn.net/hphotos-xfa1/v/t1.0-9/10302374_1646692575584761_1834228059568532121_n.png?oh=28a814fcd2c503b3e55040f852493ace&oe=56BCC378)
[IMG]https://scontent-sea1-1.xx.fbcdn.net/hphotos-xfa1/v/t1.0-9/10302374_1646692575584761_1834228059568532121_n.png?oh=28a814fcd2c503b3e55040f852493ace&oe=56BCC378[/IMG]

---

### Post by weatherman2 on 2015-10-25
If your used data will actually fit on the 120GB SSD, you can clone partition to partition if you want.  You can use Gparted in Ubuntu - a partitioning tool that also allows you to shrink and copy partitions.  However, you must first shrink a partition before you can copy it to a smaller one.  You can do the shrinking in Gparted too (that is, shrink the partitions you've just copied via ddrescue).  Gparted may or may not be installed by default in your Ubuntu live boot but I think it is on the newer versions.

The thing to remember with shrinking partitions is that you want to shrink from the END of the partition - though in your case this is probably the default action anyway in Gparted.  This can be a quick operation or it could take a while if the original partition is pretty full or badly fragmented.  Data near the end of the original partition - will have to be moved into free space to get under the new 100GB (for example - or whatever it turns out to be) boundary are shrinking to.

Anyway, decide your new partition scheme first on the new SSD.  Create the new partitions there.  Shrink the originals to fit.  Then copy them one by one with Gparted - right-click the original and choose "copy" then choose "paste" on the new partition.  This will be faster than dd/ddrescue, because it will copy only used space not everything in the partition like ddrescue does.

Finally, you'll need to dig up a Windows boot disc if you have one, drop into a command prompt, and do these commands on the new SSD once you've copied everything:

```
bootrec.exe /fixboot
bootrec.exe /fixmbr

```

If you're lucky, that will be enough to get the new SSD to boot.  You can try a Windows boot discs's automatic "boot repair" function too.

There may be free cloning tools that will shrink-and-clone automatically but I'm not aware of any.  Clonezilla won't clone to a smaller disk/smaller partitions the last time I tried it.  I have recently used a paid version of a tool called True Image from Acronis (not free but it is Linux-based) that will clone to a smaller disk automatically if there is enough room.  I used it a few months ago - version 2012 - and it was super easy to do.  I used the True Image "rescue CD" so I didn't need a working Windows installation to do the clone, though True Image is software otherwise designed to install in Windows.  Perhaps there's a way to obtain just the rescue CD ISO image for free somehow, because you don't need to install True Image itself at all to do the clone.

By the way, you might also want to run chkdsk on the cloned NTFS partition(s) too to fix file system errors caused by corrupted files due to bad sectors.

---

### Post by The Cog on 2015-10-25
Boot windows and shrink the NTFS partition on the 500G drive until the entire used part of the drive is less than 120G with the remainder unused. Windows disk manager should be able to do the shrinking. Now you can use dd or ddrescue to clone the 500G disk to the 120G SSD. It will of course bomb out when it runs to the end of the 120G SSD, but by then everything you need (the partition table and three partitions) will have been copied. The SSD should now be bootable.

It is better to let windows resize NTFS partitions than ask gparted. Gparted is good, but the NTFS filesystem is not documented and gparted has to use what knowledge has been gleaned from reverse engineering.

---

### Post by weatherman2 on 2015-10-25
I've resized plenty of NTFS partitions with Gparted.  Never had an issue.

It seems a bit more safe to me to copy partitions one at a time safely with Gparted and then do the Windows boot repair than to do a dumb dd "clone" from a larger to a smaller drive then hope it works later.

---

### Post by TheFu on 2015-10-25
To migrate to a smaller partition, I use fsarchiver.

I've been burned reducing NTFS partitions with gparted and a few other Linux tools to where Windows refused to boot. My rule is to only use tools written FOR THE OS to handle file system stuff on that OS.

Did anyone mention the different sector sizes and performance considerations if the sector alignments aren't setup correctly?

---

### Post by The Cog on 2015-10-26
> **TheFu said:**
> To migrate to a smaller partition, I use fsarchiver.
I had forgotten about that one. If you are going to just replicate a partition, that is a good bet. 
I have used it in the past to save and restore both windows and linux partitions.
> Did anyone mention the different sector sizes and performance considerations if the sector alignments aren't setup correctly?
Nope. That would be one good reason to go for manually setting up the partition tables, replicating partition contents (fsarchiver?) and then fixing up the bootloader.

---

