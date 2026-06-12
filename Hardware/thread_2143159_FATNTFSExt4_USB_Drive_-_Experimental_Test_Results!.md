---
title: "FAT/NTFS/Ext4 USB Drive - Experimental Test Results!"
date: 2013-05-08
forum: Hardware
---

### Post by afz12 on 2013-05-08
Which is the best format for a USB drive? I tested a 500 GB USB-2 hard drive using Ubuntu 13.04. Here are my speed / access time results,

Format.........FAT32........NTFS........Ext4.......Units

Read Speed...27.5.........27.8.........28.0........MB/s
Write Speed..21.5.........21.7..........21.3.......MB/s
Access Time..17.47.......17.52.........17.35.....ms

So is there any real difference here? The differences are small and I suspect that if I did a re-test, the differences would change around. So which is the best format?

I use Ubuntu, Mint and Virtualbox for XP. All work OK with any of these formats. Perhaps FAT32 and NTFS may need degrags whilst Ext4 does not - is this correct? To defrag I'd have to do this through a XP VM. What other criteria differentiate these formats?

Thanks in advance!

---

### Post by kurt18947 on 2013-05-08
I think it depends on if you think you'll want to access files on this drive from Windows.  If so, I'd probably format it to NTFS.  If not, Ext4 seems pretty stable these days.  FAT32 has the 4 GB. file size restriction and  I don't believe FAT32 is as error tolerant as NTFS.   NTFS partitions seem to read and write reliable as long as the required NTFS utilities are installed on linux O.S.s.    There are Windows drivers available that enable reading ext* file systems.  Writing to ext* file systems from Windows seems a dicy proposition at this point.

---

### Post by Cheesemill on 2013-05-08
Best is a very subjective word. It all depends on what you are going to use the USB drive for, speed is only one of the factors to consider. Here are a couple of other things to consider...


[LIST]
[*]If you don't need access from a Windows machine then go for ext4. Because it's a native filesystem it's the only one that supports the Linux permissions structure properly.
[*]If you don't have access to a Windows machine then don't go for NTFS, as there are certain filesystem problems that can occur that can only be fixed from a Windows machine (using chkdsk).
[*]Certain hardware can only read FAT32. For example smart TV's, car audio players, printers etc.
[*]FAT32 has a maximum file size limit of 4GB (minus 1 byte).
[/LIST]

---

### Post by oldfred on 2013-05-08
You have to run chkdsk on FAT32 and because it does not have a journal it can be slow to run chkdsk or not recover as much.
FAT32 is really for smaller partitions like you might have on your 2GB or 4GB flash drives. But now that even those are much larger and the device may only support FAT32 you may have to use it.

But if you have a choice use NTFS if you want compatibility with Windows.

---

### Post by afz12 on 2013-05-08
Thanks for the replies. However I think FAT16 is limited to 4 GB, I quite easily format much larger drives to FAT32 - e.g. 16 GB USB flash drives. I have an older notebook that uses FAT32 on a 30 GB hard drive - as per it's manufacturer. However I note that RAM access is limited to less than 4 GB using FAT - perhaps external drives are different?

I intend to use the drive(s) with Linux but I use Windows from time to time as a Virtual Machine. These VM's seem to run data on or from any format.

I think I prefer Ext4 as I've read that this format doesn't need defragging. Otherwise I can't see any real advantage to FAT32 except that the Ubuntu formatter etc claims that it is compatible with any OS!.

I have no interest in games, ipods or otherwise. I "might" want to connect to a windows box at some later date but then I think it would be just as easy to transfer any particular disk seqment I want to memory stick. 

Anyway, I had been curious for some time if there were any "killer" advantages between one format or another but it seems that any differences are eeither minor or dependent on whether the dominant application is Linux or Windows. Since my notebook's run Ubuntu and/or Mint and I use Virtualbox for anything else, I may as well format to Ext4!

Thanks for the replies.

---

### Post by kurt18947 on 2013-05-09
> **afz12 said:**
> Thanks for the replies. However I think FAT16 is limited to 4 GB, I quite easily format much larger drives to FAT32 - e.g. 16 GB USB flash drives. I have an older notebook that uses FAT32 on a 30 GB hard drive - as per it's manufacturer. However I note that RAM access is limited to less than 4 GB using FAT - perhaps external drives are different?
<snip>

Thanks for the replies.

AFAIK FAT32 *file* size is limited to 4 GB. minus 1 byte.  Fat 32 *Partition* size appears limited to 32 GB. without the use of a 3rd party utility.

[http://www.techrepublic.com/blog/window-on-windows/format-fat32-drives-beyond-32gb-limit/5693](http://www.techrepublic.com/blog/window-on-windows/format-fat32-drives-beyond-32gb-limit/5693)

I wonder what file system flash drives larger than 32 GB. use?   NTFS?  ExFAT?

Re system RAM, here is an article about 32 bit O.S. RAM limitations:

[http://www.zdnet.com/blog/hardware/clearing-up-the-3264-bit-memory-limit-confusion/3124](http://www.zdnet.com/blog/hardware/clearing-up-the-3264-bit-memory-limit-confusion/3124)

To further confuse the issue :P

[http://msdn.microsoft.com/en-us/library/windows/desktop/aa366778%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa366778%28v=vs.85%29.aspx)

---

### Post by afz12 on 2013-05-09
Hi kurt18947. Thanks for the links - much appreciated! My notebook also has a SD card port and I can format a 30 GB SD card to either FAT32, NTFS or Ext4 and it works properly on all 3 formats. Later on, I plan to get a 64 bit SD card and I suspect that FAT32 will be limited to 32 GB as you suggest!

When I try to format these USB drives in Windows, for example, there are options for segment sizes - I suspect that small chunks of RAM are used to map out the entire content (i.e. the whole drive is not read/written to in one chunk). This may be why an external drive can be formatted quite well with FAT32 up to at least 30 GB or 32 GB as you explain. I wonder why this might be a limit given that I had no problem formatting a 500 GB hard drive to FAT32. Admittedly I didn't test its actual storage capability though.

I also suspect that when internal RAM is added, the computer will access this directly and therefore may be address line limited. If this is 12-bit then 4,096-1 combinations are possible. Why should even an old 16 bit computer have used 12-bit rather than a more obvious 16-bit address space? Previous machines were all 32-bit, now 64-bit is common. I am coming to think that, at least, FAT32 is no use except for some specialised compatibility requirement with esoteric operating systems. Also, NTFS seems OK but it needs regular defragging and doesn't this require Windows? My current thinking is that Ext4 is the best format and can be accessed by Windows if this is run as a Virtual Machine on LInux (set up as a shared folder rather than loaded as a USB port). 

In any case, I had hoped the topic would be interesting to our members and that the real data I provided would prompt some thought and discussion.

---

### Post by kurt18947 on 2013-05-10
You don't need a virtual machine to read Ext4 in Windows.  There are Windows add-ons that can access ext4 partitions.  Here are 3 choices:

[http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

---

### Post by afz12 on 2013-05-10
Thanks for the info kurt18947. I only use a VM because this notebook only runs Linux. My older notebook can run windows natively but I seldom use it now. I am sure there are many ways to read Ext4 from many other OS.

On the subject still wrt with format is best? I started to load a 1 TB USB hard drive formatted to NTFS and looked at it via Windows XP as a VM (as this is the main way I ever use XP of course). I looked at its defrag status an what a mess! I tried to defrag it per se and one hour later it was still winding its files around! It seems, based on how things have evolved so far, that NTFS might be "better" than FAT but the need to defrag NTFS is a mission from hades. I formatted the 1 TB USB drive to Ext4 and am now loading it up. So far, Ext4 seems to be the winner.

One other observation, unfortunately uncontrolled, is that I have often noticed that the reported transfer rate falls off over time when large transfers are attempted. With NTFS I have noticed 22 MB/s fall down to a miserly 10 MB/s or so. However this 1 TB USB hard drive has remained accepting data transfer at a steady 23 MB/s for over half an hour.

One thing still surprises me. The USB2 standard claims 480 Mbit/s transfer rate (max) which at 8 bits per byte should allow 60 MB/s transfer rates. The current real-world transfer rate is 23 MB/s - obviously hard drive limited. Given this, why on earth include a much faster USB3 port on the device when the hard drive is the data-rate bottle neck, certainly not the USB version? I am certainly interested to hear anyone's explanations!

---

### Post by Cheesemill on 2013-05-10
It's not the hard drive that's the bottleneck, it's the USB connection.

A USB2 connection has an effective throughput of around 35MB/s after you take overheads into account, even the slowest mechanical drives can shift data faster than this. USB3 ups this to around 400MB/s.

---

### Post by afz12 on 2013-05-10
Thanks Cheesemill. I had wondered about this for quite some time - so much for 480 Mbit/s! My 1 TB USB drive uses USB3 so when I upgrade my notebook fro USB2 to USB3, I should be able to make use of this improved transfer rate.

---

