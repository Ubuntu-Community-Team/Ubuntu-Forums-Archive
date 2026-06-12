---
title: "Problem with external HDD"
date: 2010-11-24
forum: Hardware
---

### Post by Nozone on 2010-11-24
Hi all,

I'll just clarify first that I've already sought help from general hardware & windows support info to no avail.

I have a Medion Drive-n-go external HDD (formatted to 'msdos'), it has worked fine for a year or so on both Windows and Ubuntu. However, I recently plugged it in to a desktop with Windows installed (that the drive previously worked with) and all it does is make a 'click click beep' sound repeatedly. I searched around for some help with this and it seems that similar problems occur (particularly with Medion drives) as a result of poor soldering/poor USB connector on the drive, so I was planning to take it apart and re-house the drive.

However, I forgot that it was not working and today plugged it into my laptop which is running Ubuntu 10.10 and it works fine. I initially presumed that it must be a hardware malfunction, particularly as the drive had been in transit prior to me discovering the problem, however I don't understand why it works with Ubuntu but not Windows, and if someone could give me a few pointers or suggestions as to what this problem might be it would be greatly appreciated.

I also appreciate that this problem is most likely to do with the hardware or windows, but I've not had much luck.

Thanks for the help guys

---

### Post by oldfred on 2010-11-25
msdos or MBR is the type of partitioning. You must have a NTFS partition if you can read from windows.

Have you recently run chkdsk on the NTFS partition? Linux runs fsck every 30 or 40 boots. You should do the same on all NTFS partitions.

If also could be your loose connection is temporarily working again. I would make sure I have good backups  in any case.

---

### Post by Nozone on 2010-11-25
Thanks for your reply oldfred,

It has one partition formatted to FAT32. I've just run fsck on it and nothing has been picked up.

I've also been plugging it into both Ubuntu and various computers running under Windows, and for any Windows system it does the 'click click beep' noise. I suppose this doesn't necessarily mean that it's not the connection as I am physically moving it around, so I think I will try rehousing it to see if that resolves the problem.

Thanks again for your help

---

### Post by dandnsmith on 2010-11-25
If it works on linux systems, but not on any of several Windows systems, then the finger seems to be pointing at the HDD content (rather than the housing or cabling).
I'd suspect a problem in the area of the partition table or the FAT index. Windows is more choosy in these respects, where linux can just say..

ho hum, a minor problem, I'll just check the alternative data (for drive, FAT table etc) and try that instead.

There are tools for doing things like restoring the master FAT table from the backup copy (which Windows creates, but never seems to use intelligently). Alas that my memory doesn't come up with names of tools (its been several years since I had to recover from such a situation).

---

### Post by Nozone on 2010-11-26
Hi dandnsmith,

Thanks for your reply. I've got a little bit of feedback that might be useful in terms of your reply.

I backed up all my data on the external HD in question and then formatted it to FAT (I didn't read your post before I did this otherwise I would have had a look around for the tools required to do what you suggest. Anyway, after formatting it's still giving me the 'click click beep' noise at a reduced speed.

Will having formatted it mean it's not worth attempting the restore method you suggest, or should I give that a try anyway?

On a slight aside I can 100% it was not an issue with the enclosure/USB connection which I I thought was a long shot anyway, but on the plus side I have a fancy new enclosure.

It has also just dawned on me that if the drive doesn't have problems being picked up by Ubuntu, and I can't resolve the problem, I could just switch the external with my laptop internal.

Would I go about this as usual - add the drive, format & partition, install Ubuntu - or is there anything extra I would need to do to make it a boot drive

Thanks for your help so far all, it is much appreciated

---

### Post by oldfred on 2010-11-26
If working with more than one drive you have to pay attention to where grub is installed. It will usually default to sda, even if you are installing into sdb.

With Maverick they changed the advanced button that let you choose where to install grub to a combo box but it is only available if you use manual partitioning. So you have to use manual partitioning if you have more than one drive.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by dandnsmith on 2010-11-26
In this case, to try to eliminate the problem causing the click click beep, you'd have to take fairly extreme measures.
At very least you'd need to totally zero the sector where the partition table is (which also contains info about the disk organisation that Windows uses, but not usually linux).

For this I do a dd, with a zero source.
I haven't time to look up to get the command correct just now (visitors arriving), but can do it tomorrow if you request it.

---

