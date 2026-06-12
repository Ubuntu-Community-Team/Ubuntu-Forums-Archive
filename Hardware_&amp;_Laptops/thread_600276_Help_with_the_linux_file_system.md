---
title: "Help with the linux file system"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by FooAtari on 2007-11-02
I am building a new linux PC.  This will become my main PC holding all my docs, pictures, music, videos etc etc.  My Windows PC will be relegated to games use only.  This is the first time I have totally moved away from windows for my day to day computing.  I've tried Linux a couple of time, and it running on my laptop, but all my files have always remained on the windows PC

I have a couple of questions.  When I have only had one hard drive I have always partitioned it, keeping all my important files on a separate partition to the one windows is installed on, so that if windows died and I needed to reformat the windows partition I was fairly safe to do so without losing everything, it was certainly easier than having everything on one partition.  This would show up in windows as a separate hard drive, drives C and D for example

Now Linux has a home directory, which can be created on a separate partition.  This in effect is the same as having two partitions on a windows computer right?  As long as I am not stupid enough to reformat the /home partition I can reinstall Linux on the / partition knowing that I am getting a completely clean install of the OS as I would formatting the C:\ on a windows PC without loosing all my files?  There isn't really any advantage to leaving the drive partitioned so linux sees its has two discs?

Second question is when it comes to having 2 hard disks.  I have a 500GB disk that will hold only my video files.  This I just need to format and then I can dump all my files on it, but as it doesn't contain partitions or folders required for Linux to run, it wont mount automatically correct? I need to do this manually or set things myself so the disk mounts when the computer boots?  Would that be the best way of working with two disks?

---

### Post by Tanker Bob on 2007-11-02
> **FooAtari said:**
> I am building a new linux PC.  This will become my main PC holding all my docs, pictures, music, videos etc etc.  My Windows PC will be relegated to games use only.  This is the first time I have totally moved away from windows for my day to day computing.  I've tried Linux a couple of time, and it running on my laptop, but all my files have always remained on the windows PC

I have a couple of questions.  When I have only had one hard drive I have always partitioned it, keeping all my important files on a separate partition to the one windows is installed on, so that if windows died and I needed to reformat the windows partition I was fairly safe to do so without losing everything, it was certainly easier than having everything on one partition.  This would show up in windows as a separate hard drive, drives C and D for example

Now Linux has a home directory, which can be created on a separate partition.  This in effect is the same as having two partitions on a windows computer right?  As long as I am not stupid enough to reformat the /home partition I can reinstall Linux on the / partition knowing that I am getting a completely clean install of the OS as I would formatting the C:\ on a windows PC without loosing all my files?  There isn't really any advantage to leaving the drive partitioned so linux sees its has two discs?

Second question is when it comes to having 2 hard disks.  I have a 500GB disk that will hold only my video files.  This I just need to format and then I can dump all my files on it, but as it doesn't contain partitions or folders required for Linux to run, it wont mount automatically correct? I need to do this manually or set things myself so the disk mounts when the computer boots?  Would that be the best way of working with two disks?
Welcome to Ubuntu. Your best bet for initial setup is to set you Windows partition to the size that you want, leaving the rest of the disk for Linux. When you install Linux, it will offer you the opportunity to partition the unused portion of the hard disk. I recommend about 10-15MB for the root or '/' partition, swap partition the size of your RAM, and the rest for /home where your data and personal settings live. That way, you can, as you say, upgrade or reinstall the OS and still preserve your data untouched.

Linux recognizes both FAT and NTFS partitions and will mount them automatically on startup. With 7.10, these will be read/write enabled. Since Windows will not recognize Linux partitions and utilities to do so are unreliable, you need to make your data drive either FAT or NTFS if it will be accessed by both Windows and Linux. Simply running the live CD will show you how the FAT/NTFS drives will work.

One other note. Linux recognizes multiple primary partitions on a drive, so there is no reason to use extended partitions for your Linux setup. In fact, doing so introduces some minor problems in mounting sequences in 7.10. All partitions on my 7.10 drive are primaries.

Hope that helps.

---

### Post by gladstone on 2007-11-02
Regarding your first question, having a separate /home partition to your / (root) partition is just that. You will have two partitions just as how you used to partition in XP. The difference is they won't "show up as two different drives; C: & D:" ala XP, they are shown as directories under the file system.

This is how I have setup my linux system and recently I moved from Ubuntu to Xubuntu. Because I wanted my system fresh again, I simply formatted my / partition (leaving my /home partition intact).

With your unformatted 500GB drive, you can simply format and partition it to your liking with gparted

sudo apt-get install gparted

---

### Post by FooAtari on 2007-11-02
I think that clears things up, thanks.

Although you managed to answer the questions Tanker Bob I think you misunderstood :)  I will have two PC's one Linux, one Windows. So no need to worry about dual booting or Linux and Windows sharing a disc.

Looks like I'm good to go.

Once more question though.

How easy is it to resize partitions.  Say I have an extended partition and once I have Linux installed I want to remove the extended partition and expand the /home partition to fill the space left?

---

### Post by Tanker Bob on 2007-11-02
GParted is your friend. Should be no problem to resize, but it's always advisable to backup your data when playing with a partition.

---

### Post by FooAtari on 2007-11-02
Sounds good. Thanks :D

---

