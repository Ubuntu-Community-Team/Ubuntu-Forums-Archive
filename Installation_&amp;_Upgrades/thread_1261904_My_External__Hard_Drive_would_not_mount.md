---
title: "My External  Hard Drive would not mount"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by hayorbahmy on 2009-09-09
Hey Fellas, My Seagate External 250GB NTFS HDD, would not mount on my jaunty.
This is what happened, I did an upgrade from intrepid to jaunty a couple of weeks ago. After I restarted the machine and I logged on to the windows vista on the system( I dualboot vista and Ubuntu), my windows could not recognize the hard disk, and I tried checking from Disk management, it was not responding. But I could see the HDD from my Ubuntu.
 I googled the problem and was advised to force the HDD to mount with ntfs-3g. I did this and after it began to complain that the HDD wasnt listed in the .hal-mtab.
I yanked the HDD off and since then I have not been able to access the hard drive from Ubuntu or WIndows.
Help me o...My Hard disk contains all my files...Am a Linux Newbie.

---

### Post by Bucky Ball on 2009-09-09
Boot Ubuntu with the hard drive off and unplugged. At your desktop, plug the usb in then switch the drive on. Anything?

If you see it there, right click on the drive and choose 'unmount'.

If not, open a terminal (Applications->Accessories) and put this in:

```
sudo blkid

```
... and post the result. Have a look if it is there.

If you 'yanked' the drive out with out unmounting it or in Windows closing the drive and unplugging the usb then the drive is 'open' and therefore not recognised.

---

### Post by hayorbahmy on 2009-09-25
@Bucky Ball...am so sorry this is coming very late...av been outta town

This is d result of sudo blkid

hayorbahmy@ubuntu:/etc$ sudo blkid
[sudo] password for hayorbahmy: 
/dev/loop0: UUID="02703b21-00f7-4984-b51c-e7d3953e20c2" TYPE="ext3" 
/dev/sda1: UUID="5C44C4595AB00B44" TYPE="ntfs" 
/dev/sda2: LABEL="HP_TOOLS" UUID="EE27-0A47" TYPE="vfat" 
/dev/sda3: UUID="4064B29264B28A64" LABEL="HP_RECOVERY" TYPE="ntfs" 

The external HDD is not there...so what's next?

---

### Post by BillJohnson on 2009-09-27
Same problem here. Fresh install of Jaunty. All updates. Neither an external USB drive (with NTFS) or a NTFS partition on the same drive that Jaunty is running from is recognized. It's like Jaunty knows nothing about NTFS partitions or drives. Help....

bjohnson@bjohnson-homedesktop:~$ sudo blkid

/dev/sda1: TYPE="swap" UUID="6bd7584e-454a-4011-8afd-3c38fdace70b" 
/dev/sda2: UUID="244017C540179D1C" LABEL="DOCUMENTS" TYPE="ntfs" 
/dev/sda3: UUID="b0e819ee-c30b-4022-81af-458c2f10f61d" TYPE="ext3" 
/dev/sdb1: LABEL="03-SEP-2004" UUID="0000-0EB4" TYPE="vfat"

---

### Post by red_spyder on 2009-09-27
I've had a similar problem before. I fixed mine by connecting the hard drive to a different computer, preferably with windows. If it can open on there, just unmount it properly, then try it again on Ubuntu. It had worked for me. Apparently Ubuntu does not like it when the HDD was not stopped properly(?)

---

### Post by BillJohnson on 2009-09-27
> **red_spyder said:**
> I've had a similar problem before. I fixed mine by connecting the hard drive to a different computer, preferably with windows. If it can open on there, just unmount it properly, then try it again on Ubuntu. It had worked for me. Apparently Ubuntu does not like it when the HDD was not stopped properly(?)

Thanks,
But both of these drives work just find on a Windows XP box... waiting for an answer that makes sense.

---

### Post by BillJohnson on 2009-09-27
Problem solved. I switched to 8.04 LTS. Using EXACTLY the same hardware, everything works as it should. And now, I just read that the latest Jaunty kernel update breaks FAT/FAT32: 

[http://ubuntuforums.org/showthread.php?t=1265238&highlight=ntfs+jaunty](http://ubuntuforums.org/showthread.php?t=1265238&highlight=ntfs+jaunty)

Jaunty = poor/unusable release.

I am constantly amazed at how previous functionality breaks with a new release. I have no faith in any Ubuntu release unless it's an LTS release and has a couple of month's worth of patches on it.

Additional thoughts:
At some point, an Operating System needs to "Just Work". Note to developers: Not all of us enjoy toying with the OS every single day. Some days we would actually like to get some of our work done, instead of screwing around with stuff that doesn't work.

---

### Post by Bucky Ball on 2009-09-28
> **BillJohnson said:**
>  Not all of us enjoy toying with the OS every single day. Some days we would actually like to get some of our work done, instead of screwing around with stuff that doesn't work.

Install 8.04 LTS. If you are running a production machine, as it appears, this is recommended. In my experience rock solid.

Yep, 9.04 has been around since April and there still seems to be problems. I waited 6 months after 8.04 came out before I installed that. My computers MUST be stable for the better part of the year.

If you have a spare partition or computer Jaunty or Karmic would be the go for fiddling around with whilst 8.04 is the workhorse.

---

