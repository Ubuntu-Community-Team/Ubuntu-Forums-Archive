---
title: "Portable external hard drives"
date: 2012-03-24
forum: Hardware
---

### Post by L R C on 2012-03-24
I'm looking to buy a portable external hard drive, around the 320-500GB mark, and preferably one that is available on this site:

[http://www.pcworld.co.uk/gbuk/portable-external-hard-drives/720_7064_70069_xx_xx/xx-criteria.html](http://www.pcworld.co.uk/gbuk/portable-external-hard-drives/720_7064_70069_xx_xx/xx-criteria.html)

I know most external hard drives won't work with Ubuntu without formatting them and changing something (can't remember off the top of my head), but will they then work with Windows?

Basically I'm asking if anyone knows if any of the hard drives on the above website will work with both Ubuntu and Windows without changing any of the settings, and if not, if it is possible to format an external hard drive to work with both operating systems.

Thanks in advance.

---

### Post by Paddy Landau on 2012-03-24
Usually, the drives come pre-formatted (in my experience with FAT32, but they may be NTFS).

These will work with Ubuntu, because Ubuntu can read Windows-compatible formats.

If you want, you can reformat it yourself to a different. I format my drives with two or more partitions (depending on what I use them for): NTFS for anything that Windows and Ubuntu must share, and ext4 for anything that only Ubuntu needs.

Generally, NTFS is preferable to FAT32.

---

### Post by L R C on 2012-03-24
> **Paddy Landau said:**
> Usually, the drives come pre-formatted (in my experience with FAT32, but they may be NTFS).

These will work with Ubuntu, because Ubuntu can read Windows-compatible formats.

If you want, you can reformat it yourself to a different. I format my drives with two or more partitions (depending on what I use them for): NTFS for anything that Windows and Ubuntu must share, and ext4 for anything that only Ubuntu needs.

Generally, NTFS is preferable to FAT32.

So I could use any Windows-compatible hard drive with Ubuntu without reformatting? Although I probably would...

Thanks for the help man!

---

### Post by jmore9 on 2012-03-24
I just use an 160 gig I think it is.  It is an laptop drive i had ordered by mistake , i have no laptop !  So i just ordered a external usb converter , which is a small box with caps on each end.  And put the drive in it.  It cam with a cable to connect to the computers usb port and has worked fine for about 2 1/2 years now.  I orginally used it with winxp so it is formatted as NTFS but is being used with linux now with now problems at all.

Hope that helps.

---

### Post by efflandt on 2012-03-24
Whether you would need to reformat anything depends whether you are going to want to boot Ubuntu from the external drive or not.  If you are only going to use it for data, you can likely use the drive as is.  But if it is FAT32 instead of NTFS and you want to store any files larger than 4 GB, you should probably format it in Windows, then Linux could use it just fine.

If you want to boot Linux from the external drive, you would want to repartition it with appropriate file system for Linux partition(s), and the rest could be NTFS for shared data.

---

### Post by L R C on 2012-03-24
> **efflandt said:**
> Whether you would need to reformat anything depends whether you are going to want to boot Ubuntu from the external drive or not.  If you are only going to use it for data, you can likely use the drive as is.  But if it is FAT32 instead of NTFS and you want to store any files larger than 4 GB, you should probably format it in Windows, then Linux could use it just fine.

If you want to boot Linux from the external drive, you would want to repartition it with appropriate file system for Linux partition(s), and the rest could be NTFS for shared data.

I doubt I'll want to boot from it, but I might make a small partition in case I do in the future.

Would I need to download formatting software to partition/format the drive? I've got access to a computer with Windows 7 so that won't be a problem.

---

### Post by Paddy Landau on 2012-03-25
> **L R C said:**
> I doubt I'll want to boot from it, but I might make a small partition in case I do in the future.
No need. Ubuntu is perfectly capable of shrinking the existing partitions and creating new ones should you need to in the future. I have done it several times.

> **L R C said:**
>  Would I need to download formatting software to partition/format the drive?
No. In Windows 7, you use the Computer Management tool (I forget where in the menu to find it). In Ubuntu, you can use either Disk Utility or GPartEd.

---

