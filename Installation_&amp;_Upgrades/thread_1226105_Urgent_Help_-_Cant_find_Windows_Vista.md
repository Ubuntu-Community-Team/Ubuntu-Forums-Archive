---
title: "Urgent Help - Cant find Windows Vista"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by mugway05 on 2009-07-29
Hi Guys,
I am very new to this whole Ubuntu stuff. A friend suggested I add it my computer as another option to Vista. I downloaded Ubuntu and saved onto a CD. I then installed Ubunta onto my computer. Whilst installing it gave the option to replace Vista or dual run both systems. As I am new to it all I didnt want to replace Windows Vista just yet.

However since I have added Ubuntu I cant get back onto Windows Vista or access any of my files I have saved on my Hard Drive (eg. photo's, movies ect.)

Can someone please help me get my Vista up and running again.

I think I may have installed Ubuntu twice and thats the reason I cant see Windows Vista any more.

Thanks heaps.

---

### Post by mikewhatever on 2009-07-29
Hi and welcome,
can you open Application->Accessories->Terminal and post the output of the following command (type in the password when asked and hit enter):

**sudo fdisk -l**

---

### Post by mugway05 on 2009-07-29
[B]Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
[/B]

---

### Post by coffeecat on 2009-07-29
I think you must have mistyped something. That's...

```
sudo fdisk -l
```Lower-case L at the end

---

### Post by mugway05 on 2009-07-29
Sorry mate:

Try this:

[FONT=monospace]mugway05@mugway05-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31f1ea89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37810   303708793+  83  Linux
/dev/sda2           37811       38913     8859847+   5  Extended
/dev/sda5           37811       38261     3622626   82  Linux swap / Solaris
/dev/sda6           38588       38891     2441848+  83  Linux
/dev/sda7           38892       38913      176683+  82  Linux swap / Solaris
/dev/sda8           38262       38565     2441848+  83  Linux
/dev/sda9           38566       38587      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order[/FONT]

---

### Post by hibliss on 2009-07-29
There is no Windows partition there, it is gone.

---

### Post by mugway05 on 2009-07-29
Ouch! Does that mean I have to reinstall it some how?

Also what about all my files on my hard drive like photo's movies ect. Have they been wiped too?

---

### Post by coffeecat on 2009-07-29
You didn't install Ubuntu twice, you did it three times! There are three ext3 partitions (for Ubuntu presumably) and three swap partitions.

> **mugway05 said:**
> Ouch! Does that mean I have to reinstall it some how?

I'm afraid so. Your Vista NTFS filesystem has been replaced

> **mugway05 said:**
> Also what about all my files on my hard drive like photo's movies ect. Have they been wiped too?

Some will have been overwritten. Others will still be there but inaccessible because the filesystem has changed. If you have no backups - please tell me you have backups - **do not boot up the computer from the hard drive**. This is to prevent any more sectors of the HD being overwritten. It may be possible to recover files with the testdisk/photorec application using a live CD, but if you're new to Linux that may be challenging.

---

### Post by mugway05 on 2009-07-29
No I didnt back up any files as I had no idea I was replacing Windows with this system and no idea it was deleting my files.

Yes I am very new to Linux so it will be challenging.

I need to get as many files as possible from hard drive. Would it be best if I take it to a computer shop and have them do it?

---

### Post by coffeecat on 2009-07-29
> **mugway05 said:**
> I need to get as many files as possible from hard drive. Would it be best if I take it to a computer shop and have them do it?

It depends on the computer shop, I guess. There are specialised data recovery businesses, but they tend to be **very** expensive.

Don't let me discourage you from trying testdisk/photorec. I was just wanting to warn you that it's not a gui-friendly straightforward app. I've only used it once in a tryout situation, so I'm not the best to talk you through it, but in outline what you do is boot up from the live CD and use Synaptic to install testdisk. You obviously need a working internet connection and you can do this live, because the testdisk app is held in RAM. You then plug an external USB drive in to save the rescued files, mount each of the Linux partitions in turn and run the photorec app to see what it can find and copy to the external drive.

That's the theory. If you want to give it a go, search the forum for threads on testdisk/photorec, or start a new help thread linking to this one. Hopefully, someone with real experience of testdisk can talk you through it.

---

### Post by mugway05 on 2009-07-29
Thanks mate I appreciate it. I have decided to give it a go.

I have 2 hard drives installed on my lap top. 

How do I find the 2nd hard drive?

---

### Post by coffeecat on 2009-07-29
Now you've lost me. Two hard drives? On a laptop? That must be a helluva laptop. :wink: I've never come across a laptop with two HDs. Can you get them with two? I didn't know.

Anyway, the output of fdisk showed only one hard drive - in Linux-speak: sda. A second drive would show up as sdb. Can you clarify what you mean, and what you mean by being able to find it? I'm logging off for a couple of hours, but I'll check this thread this evening (UK time).

Good luck!

---

### Post by GailGaby on 2009-07-30
Somebody help me please I have tried everything but Vista will not let me load Ubuntu

Ok this is what I have done

I have partitioned  the hard drive but it is not formatted but and have allotted 53 GB in the partitioned side
I have defragged
I have created an Ubuntu disk
I got into to Bios and selected the cd/dvd boot option and saved it 
nothing has worked to get Ubuntu loaded in the partitioned drive 

I have even tried the Wubi but after I down loaded it  and opened it up it started down loading then gave me an error message.

Any ideas?

---

### Post by merlinus on 2009-07-30
I strongly suggest you start your own thread rather than jumping into someone else's.  You will get more help that way as well.

---

### Post by lisati on 2009-07-30
> **GailGaby said:**
> Somebody help me please I have tried everything but Vista will not let me load Ubuntu

<snip>

Any ideas?

As merlinus has suggested, it might be a good idea to start your own thread as the problem you describe is different; it could get confusing for those of us trying to help when there are two different discussions going on. if possible include the error message (not here in mugway's thread but your own thread)

> **mugway05 said:**
> No I didnt back up any files as I had no idea I was replacing Windows with this system and no idea it was deleting my files.

Yes I am very new to Linux so it will be challenging.

I need to get as many files as possible from hard drive. Would it be best if I take it to a computer shop and have them do it?
Mental note for future: make backups of your important data. This includes recovery partitions.

Did your computer come with recovery disks or a recovery partition?

---

