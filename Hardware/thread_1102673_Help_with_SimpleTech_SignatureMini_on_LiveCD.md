---
title: "Help with SimpleTech SignatureMini on LiveCD"
date: 2009-03-21
forum: Hardware
---

### Post by seabrighter on 2009-03-21
Hello,

I'm new to ubuntu, but I've been reading about it non-stop for hours.  A friend turned me on to this because I experienced an unrecoverable windows crash.

I'm currently existing on a LiveCD of 7.04 (feisty), running the OS direct from CD.  I want to install the latest version of ubuntu, but I'm needing to back up my hard drive data before fully installing the new OS.

I have an external 250GB SimpleTech Signature Mini drive that I'm trying to migrate crucial data onto.  The Signature Mini comes with some kind of proprietary software that was restricting me from writing data to the drive.  The drive was recognized by ubuntu, so I followed [some advice]("http://ubuntuforums.org/showthread.php?t=983378&highlight=SimpleTech") to format the drive, hoping to get around this write permissions issue.

Using Gnome Partition Editor, I attempted to re-partition the drive.  I chose an ntfs partition, since this is the format of my hard drive that I need to back up (am I right to assume this?).  Gparted failed to execute the partition, however it did manage to erase the existing partition.  Now the drive has just unallocated space.

The problem is, after unplugging the drive and plugging it back in, now ubuntu no longer detects it.  I went from having a drive with no write capability to no drive at all (which I guess is the same place).  

How do I get this drive back so I can start using it to back up my data?  Can I do it using this LiveCD OS as I am now?

---

### Post by seabrighter on 2009-03-22
A little update on my progress....

So far I have figured out how to format the SignatureMini using Ubuntu.  However, every time I format it, the drive seems to be locked and will not allow me to write data on it.  At one point I had it formatted as a FAT32 drive, and I was able to write data.  However, all my data is on an NTFS drive, and I do not want to put NTFS data onto FAT32.  

Am I restricted somehow because I am using the LiveCD?  It's a catch 22 here...the only OS I have right now is the LiveCD 7.04.  I have no other way to back up my data without using this LiveCD, and if I can't back up my data then I can't install the new OS.

Can anyone help me backup my precious hard drive so I can go on with my life?  I'm feeling stuck.

---

