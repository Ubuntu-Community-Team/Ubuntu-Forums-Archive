---
title: "Gparted - Can't partition vista"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by Oberox on 2009-10-18
[ATTACH]132280[/ATTACH]

I can't figure out why I can't edit this vista partition. I'm thinking it may be because it cannot see the information inside of the partition, but when I mount it, it can....
Any help on decreasing the size of this partition. I'm trying to duel boot with vista but the partitioning is becoming bothersome. Any advice or help is welcome.

Thanks in advance. 
-Oberox

---

### Post by bulldog on 2009-10-18
The best way to do this is from disk manager in Vista.
Defrag one or better two times the vista partition and decrease the partition after that from disk manager in vista.

---

### Post by lidex on 2009-10-18
You'll need a gparted-live disk. Download one from here:[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") and burn it. You'll want to boot from the cd. From there it will allow you to resize win partition.

---

### Post by graysky on 2009-10-18
Looks to me as though you are lacking the ntfs support in gparted.

```
Optional dependencies for gparted
    e2fsprogs: for ext2/ext3 partitions
    dosfstools: for fat16/32 partitions
    jfsutils: for jfs partitions
    ntfsprogs: for ntfs partitions
    reiserfsprogs: for reiser partitions
    xfsprogs: for xfs partitions
    gksu: to run gparted directly from menu
```

---

### Post by bulldog on 2009-10-18
What I know of Vista is that it won't like to be changed by anything else but Vista.
If you persist to decrease the partition within gparted,you'll have a fair chance you damage your Vista
Just use the disk manager within Vista to decrease the partition,after you have defragged it.
Create a new partition from the free space and your done in a relative secure way.
If you make a mistake when resizing Vista to a smaller partition in gparted,it will be damaged beyond repair.

---

### Post by lidex on 2009-10-18
> **bulldog said:**
> 
If you make a mistake when resizing Vista to a smaller partition in gparted,it will be damaged beyond repair.
 
Not necessarily. I recently performed this on new HP laptop with Vista pre-installed. Resized Vista using gparted live cd. Vista would not boot so I booted into Vista cd, ran repair and worked perfectly. Vista installs files way out toward the end of the partition that it marks as unmovable so using Vista resize only allows you to shrink to that point.  

Tutorial here:[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Further: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

---

### Post by bulldog on 2009-10-18
That can be true,and I believe you,but I can't see if topic starter has such a repair disk or recovery partition.
So I tell him the safest way to decrease his Vista install.

But it's only a good thing for TS to get more options to do what he wants to do.decreasing vista,he has to make his own choice.

---

### Post by Mark Phelps on 2009-10-18
bulldog is right in what he says. lidex admitted that Gparted damaged his install and booted into a CD to repair it.

The problem is that the vast majority of folks, especially those who bought recent machine with Vista preinstalled, do NOT have the CD or DVD needed to do the repair.

So, while it may sound trivial to some to boot from a disk and run a repair -- if you don't have the disk, then Vista is "damaged beyond repair".

Given that the Vista utility does NOT damage Vista, and that it's free, and that it comes with every install of Vista, it seems to me silly to recommend something else that HAS damaged Vista -- when the safe option is already there.

---

### Post by Herman on 2009-10-18
**I agree that using Vista or Windows 7's own disk management utility seems like the fastest way to resize Vista or Windows 7**, after having tried it out.

**I also know** that we can resize Windows Vista and Windows 7 partitions using GParted quite safely regardless of their state of fragmentation.


[IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]

**The best way using GParted** would be to avoid moving the start point of the Windows Vista or 7 partition by removing the check mark from the 'round to cylinders' check box then Windows will boot right up afterwards without a hitch.

**The reason why** we should remove the check mark is because Windows Vista and Windows 7 partitions begin in sector 2048 instead of 63, which is different from tradition and rather unconventional.

**Even if we don't know or if we forget** to remove that checkmark, GParted will take a very long time and move the entire partition to the left, to make it start in sector 63 instead of 2048.
That will tie the computer up for a long time but  it won't matter much, normally Windows Vista or Windows 7 will have a slight delay the next time it tries to boot but Windows can re-adjust itself in a minute or two and reboot and will usually recover just fine.
**On some occasions** if we're unlucky, it might be necessary to use a Windows Vista or Windows 7 CD to do some automatic readjustments. The repair tool in the CD  user friendly and easy to use if you have the CD, (or DVD).
If you don't have the CD or DVD, a repair-only, (non-install) .iso image is available for free and it's only a small download, [Windows Vista Recovery Disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") from NeoSmart Technologies, (the makers or EasyBCD).

**This applies to** Windows Vista users and Windows 7 installations when Windows 7 is installed in one partition.
Windows 7 defaults to installing in two partitions, a small boot partition plus a / partition if it's installed in a disk by itself, so is more robust.

**This issue does not apply to** any of the Ubuntu installations CDs inbuilt partitioners, (at least not any that I've tested yet so far), because none of those have ever moved the start point of the Windows partition and there's no checkbox to remove the checkmark from in a Ubuntu installation CD.

Regards, Herman :)

---

### Post by Herman on 2009-10-18
Oh I forgot to mention that GParted will stimulate Windows to run CHKDSK when Windows reboots after being resized. This normally only takes a few minutes.
The GParted documentation advises running CHKDSK after resizing an NTFS partition and personally I like CHKDSK /R from a command prompt in a Windows installation/repair disk.
CHKDSK /R takes a long time and probably it does a better job.

It may be helpful to try CHKDSK /R *before* the resize as well but if you're using GParted.
Defragging before using GParted to resize an NTFS partition is probably just a waste of time, it won't make any difference to the resize operation. Defragging is usually good for Windows though. :)

---

### Post by orky7 on 2009-10-18
your dev/sda3 partition is empty so i think u formatted the vista..if u have formatted it then try to again format using ext3/ext4 and then make the partition and set the flag as boot....

---

### Post by lidex on 2009-10-18
Thanks for the enlightenment guys. My Vista disk manager would only give about 12 GB and I needed waaay more than that. For recovery I used a "Vista Anytime Upgrade" dvd that I'm not even sure how I received. Think I got it from MS for $11 without a product key. It doubles as an install disk for all versions of vista (x32 anyway). 

I gave the links because they show the different options available for Oberox to choose from. For me at least, the in-vista option was not acceptable.

---

