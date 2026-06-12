---
title: "cannot write to USB HDD"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by bradford72 on 2007-01-22
I have a Maxtor Onetouch II external, USB HDD 200 GiB attached to my system.  ubuntu tells me it is mounted at /dev/hda1 and the access path is /media/usbdisk.  There is also an icon on my desktop showing me that the system "sees" the disk, but I am unable to save any files to it. Through the terminal, I have been able to make directories on the drive through the 'sudo mkdir' command, and I'll wager that I could save files that way...but what a pain that would be to have to do that for everything!  I would like to use that drive as the default location where I save my files and any other software I may accumulate, but don't know how to go about setting things up to do that...I'm pretty new to ubuntu.  I only have 10 GiB on my internal drive, and would like to just have ubuntu on there.  I suppose it's also important to say I'm using dapper...6.06 I think

---

### Post by taurus on 2007-01-22
Does that USB harddrive have ntfs or fat32 filesystem on it?

```
sudo fdisk -l
```

---

### Post by bradford72 on 2007-01-22
I believe it is efs2....I was able to disable the drive  and format it using the 'disk management' tool by going through system->administration ...before that it was ntfs

---

### Post by bradford72 on 2007-01-22
> **bradford72 said:**
> I believe it is efs2....I was able to disable the drive  and format it using the 'disk management' tool by going through system->administration ...before that it was ntfs

I'll try to get better info....not at home with the machine right now...sorry

---

### Post by bradford72 on 2007-01-22
> **taurus said:**
> Does that USB harddrive have ntfs or fat32 filesystem on it?

```
sudo fdisk -l
```

Well, paint me red and call me embarassed...this is what it said:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24792   199141708+   7  HPFS/NTFS

I'm guessing that means it's ntfs...:roll:

---

### Post by Triple Threat on 2007-10-07
I am having the same problem. My external HDD is a USB with Fat32 or vFat or w/e (not NTFS basically) I fixed some of the problems like being able to drag and drop files onto the drive. I used to get an error when doing that. What I did to fix it was add my user to the plugdev group. Unfortunately, this didn't fix all of my problems. When using Fire Fox (and maybe any tool that lets you download files) I cannot download files on to the drive.

Now this is the important part: It **CREATES** the file, but doesn't **WRITE** to it.

I have a short cut on my on my desktop that lets me view the properties of the drive. I think I can fix all of my problems if I can change the group from root to something else, like my user group or plugdev. The problem is that it tells me I dont have the permission to do this. If I could run this window as root I think my problem can be solved. How would I go about doing that?

Thanks in Advance.

---

