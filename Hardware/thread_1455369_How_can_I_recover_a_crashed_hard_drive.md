---
title: "How can I recover a crashed hard drive?"
date: 2010-04-15
forum: Hardware
---

### Post by dcor on 2010-04-15
Hello,

My girlfriend's laptop hard drive died, and I would like to try and recover as much data as I can from it. I'm not sure what type of file system it had, but it had Windows installed, so I guess that is NTFS? I got an external enclosure and hooked up the drive via USB, but I cannot even see the drive in Windows or Linux. If you could give me any tips or point me in the right direction I would really appreciate it. I am new to Linux, and I do not fully understand mounting.

Thank you,
Derek

---

### Post by dcor on 2010-04-16
I have heard of a program called DD, but when I plug in the hard drive I'm not sure where the device is. I heard it's supposed to be in /media, but I cannot find it.

---

### Post by 2hot6ft2 on 2010-04-16
This is your best shot.

[How to: Recover data with testdisk!]("http://ubuntuforums.org/showthread.php?t=387922")

P.S. DD is short for DataDump and is used in the terminal but if the drive can't be read normally you would only be duplicating the problem to a second drive by using dd to clone it.

---

### Post by buntudawg on 2010-04-16
Hi

have you tried this thread:

[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by 2hot6ft2 on 2010-04-16
> **buntudawg said:**
> Hi

have you tried this thread:

[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)
A valid point since windows will NOT see another version of windows (it auto hides it to prevent conflicts). And you would need the support in ubuntu for NTFS which it sounds like you may not have set up. I would say try this before trying testdisk.

---

### Post by dcor on 2010-04-16
Thanks for the replies.

@ buntudawg:

I tried ntfs-config and it wasn't able to recognize the external laptop drive.

@ 2hot6ft2:

I tried test disk, but once again it could not find the drive.

I've never used an external HD before, it there anything I need to do besides plugging it in? Is there anything left I can try, or is this drive toast?

---

### Post by paulisdead on 2010-04-16
The drive should show up somewhere in the /dev/ directory and will probably be associated with a device node like /dev/sdb and have partitions like /dev/sdb1.  The letter might be different and you can run 'dmesg' in the command line without the quotes to see if the kernel detected any new devices.  If you just plugged the drive in, anything associated with it should be at the bottom of the output and easier to find the relevant info for the drive.  If it's not getting a device node, the errors might give you some direction to go in.

You might want to try ddrescue, it's a version of dd designed to work on a failing drive, and will repeatedly keep trying in places where the regular dd would give up.  Just to be clear what both dd and ddrescue are used for in these cases, is to make an image of the drive, so you can then try to mount the image and work from that instead of directly working from the failed drive.  Since you're making an image of the drive, you need to be sure to dump it to somewhere that has enough space.

You can apt-get install ddrescue, and I'm sure there directions if you just google ddrescue.  You probably want to use it on the individual partition and not the whole drive, to make mounting it easier.

---

### Post by 2hot6ft2 on 2010-04-16
Well if it has the jumper to change it from Master/Slave/Cable Select it needs to be set to Master when you use it in an external usb housing.

Have you tried the xp recovery cd?
If you don't have one I think the vista one works with xp too and you can get one here for free
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
You would have to put the drive back in the pc and boot from the recovery cd (while keeping your fingers crossed).

Tough to fix or get anything off of if the system doesn't even see it.

---

### Post by dcor on 2010-04-16
@ paulisdead:

I checked dmesg as well as the /dev directory, but there are no changes when I plug in the hard drive.

@ 2hot6ft2:

There aren't any jumpers I can change from what I can see. Also, I only have Windows 7. Does the Windows 7 CD function as a recovery CD too?

Thanks.

---

### Post by dcor on 2010-04-18
Does anyone have any ideas?

---

### Post by camdude on 2010-04-18
If nothing can read the drive, than it is a Harddrive failure, not the software. Recovering Data from Hard Drive failures is very expensive, and is usually unsuccessful in getting even 80% of your data back, and the data you do get back is often corrupted, and you need to delete it anyway. 
PS: The Harddrive is junk, you might be able to recover data, but not the HD

---

### Post by dcor on 2010-04-18
Ok I have good news! After putting the hard drive for a few hours in the freezer, I am able to pull data off of it using photorec. Since the file names aren't restored, and it gives just a huge file dump, when that is done I want to see if I can actually access the NTFS partition.

Note that the hard drive has Linux and Windows on it. 

When I plug it into Windows, it cannot find the partition and tells me to format it. When I plug it into Linux, it can see the Linux partition and I can access those files fine. However, I cannot seem to mount the NTFS partition at /dev/sdb1. Each time I try it gives me an error saying its corrupt.

Is there any way to restore the Windows partition so I can mount it and grab the files?


Thanks!
Derek

---

### Post by 2hot6ft2 on 2010-04-18
> **dcor said:**
> Does the Windows 7 CD function as a recovery CD too?

Yes it can.
When you plug a drive with windows on it into windows. Windows will HIDE the second windows install so it's not seen. That's why windows wont see it. It's windows way of making sure it doesn't get confused as to which set of files it's supposed to be using to run. Don't you just love that.

If the windows 7 cd can't see it then it will just want you to format it like you already said, but it may ask you if you want to repair it.

---

### Post by dcor on 2010-04-18
@ 2hot6ft2:

Will reformatting it erase the contents of the hard drive?

---

### Post by camdude on 2010-04-18
unfortunately, yes it will... but if you can retrieve data after putting the HD in the freezer, you might be able to take it for repair, because it might be the lubricant that needs to be replaced (which has happened 2 me twice) what kind of noise does the HD make when started up (if any)?

---

### Post by 2hot6ft2 on 2010-04-18
> **dcor said:**
> @ 2hot6ft2:

Will reformatting it erase the contents of the hard drive?
It sure will.

Since the drive may be dead anyway you may as well try everything you can before resorting to reformatting it at which point everything on it should be considered gone for good if it hasn't been recovered.

Once you get to that point I would only use it as a secondary drive and wouldn't put my OS's on it again since it may happen again depending on what actually led up to the situation you're in with it now.
A couple of my 15+ drives were once used for Operating Systems but I don't trust them that much anymore so now they only store secondary backup info. A backup is nice to have and 2 backups are even better (a backed up backup)...

---

### Post by Zer0Nin3r on 2010-07-29
What if your home directory is encrypted?


**UPDATE**

I figured out that my hard drive is failing and that I needed to use the rescue disk from Western Digital.  With that I was able to rescan the hard drive and reset the error code.

---

