---
title: "5 Hard Drive + 1 Ubuntu = Problem"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by Boneybone on 2009-04-07
Hello folks, I've been reading for over a week to find a solution to a specific problem of mine but failing miserably. Let me explain the situation...

**Linux knowledge, experience:** N/A
**Current OS:** Windows XP Professional
**Main Hard Drive:** 250 GB
**Slave 1:** 160 GB (full-internal)
**Slave 2:** 160 GB (full-internal)
**Slave 3:** 40 GB (full-internal)
**Slave 4:** 1 TB (full-external via USB, Western Digital My Book)

**Want to:**

**01.** _format Main HD and install latest Ubuntu_
**02.** keep other 4 slaves _untouched_ during installation process
**03.** use Ubuntu as one and only OS on this very PC
**04.** keep access to the data on those 4 slaves(NTFS)
**05.** being able to modify those 4 slaves _without formatting anything_ like file system because, read below (modify as in add other files, delete some etc.)
**06.** keep those 4 slaves usable on other PCs (as in plug-out from my PC that runs Ubuntu, plug-in to other PC that runs Windows so that machine can access the files and privilage of adding, removing files from it; basically using it as its own slave)

All I need to install Ubuntu is present but the process currently stays on hold because I'm afraid of losing the data on the 4 slaves while installing Ubuntu.

In windows, one can install the OS on drive "C" and other slaves "D, E, G etc." remains untouched during the process and after finalizing the installation of the OS, all the physical hard drives, slaves, are already there, ready to use with the data in them. We can move, copy files from one to another and add new files to any one of them et cetera...

That, is what I am trying to accomplish with the Ubuntu.

I hope the problem I'm experiencing is explained well enough for you folks to understand and help me through this.

---

### Post by jo4hnc on 2009-04-07
Why don't you disconnect all but your main drive, install Ubuntu and then reconnect the drives. I really don't think that an install will have any effect on your data but disconnection might give you some piece of mind.

You may have to set permissions for the other drives after the install and then reconnection.

---

### Post by Boneybone on 2009-04-07
I thought about disconnecting all the slaves but what about after the Ubuntu installation?

I've read on Ubuntu website that, Ubuntu uses different file system compared to Windows NTFS and there are no distinction between physical hard drives and Ubuntu sees all the hard drives under the same folder. So if I connect my 4 slaves after installation, Ubuntu going to mix other 4 with the main drive but they have different file system.

How can I use different hard drives with different file systems under a single OS? If I change the file system, which means formatting the hard drive, all the data will be lost. If I don't, how can I add a file to that hard drive if it's a different file system.

When I plug-in my external hard drive to my laptop, I can add or remove files from it or use the files on it. If it's not a NTFS format, that wouldn't be possible. 

I'm pretty sure I'm missing something about this issue. It can't be this complicated.

---

### Post by dandnsmith on 2009-04-07
> **Boneybone said:**
> I thought about disconnecting all the slaves but what about after the Ubuntu installation?

I've read on Ubuntu website that, Ubuntu uses different file system compared to Windows NTFS and there are no distinction between physical hard drives and Ubuntu sees all the hard drives under the same folder. So if I connect my 4 slaves after installation, Ubuntu going to mix other 4 with the main drive but they have different file system.

The issue is whether ubuntu can read the files in that type of filesystem - it doesn't matter that they are of different format; linux will sort that out.

> How can I use different hard drives with different file systems under a single OS? If I change the file system, which means formatting the hard drive, all the data will be lost. If I don't, how can I add a file to that hard drive if it's a different file system.
linux sorts that out - it knows what sort of format is needed and uses it.

> When I plug-in my external hard drive to my laptop, I can add or remove files from it or use the files on it. If it's not a NTFS format, that wouldn't be possible. 
Yes, it would. Linux has been able to do this ever since its inception, starting with using FAT, and adding features for other types during development.

> I'm pretty sure I'm missing something about this issue. It can't be this complicated.
It really isn't that complicated. Your view of it is what hampers you.
Each mounted filesystem is handled in the way it needs, despite the method of making it look integrated - Windows is the odd man out here, making differences where there don't need to be.

The real problem you might have is that the tools you use with your ubuntu install to write to an NTFS filesystem cannot be guaranteed to be compatible with the way Windows will see things. This is because NTFS is a Msoft proprietary filesystem representation, which they can alter at will - one manifestation of this is the fact that Vista can 'corrupt' such a filesystem from the XP point of view.

The only safe way to get transferrable data is to use an industry standard format (eg FAT filesystem), which both can use.

---

### Post by Boneybone on 2009-04-08
After reading your post, Derek, I searched the internet about information regarding filesystems which I thought I knew all about...

Couple of hours later, I was installing Ubuntu 8.10 to my main hard drive via DVD I burned. I would like to write my experience, in case someone stumbles upon this thread, seeking solutions. I've encountered a couple of problems with the installation...

-Changed boot sequence from the setup, DVD already in the drive, reboot.

-Installation menu, pretty straight forward.

-I choosed use entire disk, 250GB SATA. (All my hard drives are single partition)

-Installation process completed, told me to remove CD and reboot.

-I did, then hit "del" got into setup, changed primary boot source to HD, save and reboot.

-DISK BOOT FAILURE, great.

-After a couple of this-is-going-to-work-if-I-keep-doing-nothing-but-rebooting moments, I looked on-line for the Ubuntu boot sequence.

-While I was reading what happens on the background when Ubuntu loading, I saw something called Grub.

-Looked what that is exactly and realized I do, in fact, not have that on my computer even though it should be there because Ubuntu DVD has to include that in the intallation. Oh well...

-Went back into setup, changed the primary boot source to CD-ROM again. Slapped the Ubuntu DVD back in.

-Did everything all over, my name is, location, use entire disk, stare at the progress bar and finally remove the CD and restart page.

-This time, I did what it exactly told me to, didn't get back into setup and change the boot order, it still is CD-ROM then HD, actually.

-Grub jumped in this time instead of bailing out and there it is, my Ubuntu desktop.

-I was very anxious to setup my wireless, sound card, GPU and al the other bits but unfortunately I couldn't.

-They were already working, brilliant.

-Ubuntu needed updates, 20 mins later everything worked.

**Adding slave drives:**

Surprisingly, they were already there untouched, right click and hit "mount" is suffice to gain access to all the data.

No problems at all.

Actually, I felt a little disappointed for not encountering any problems.

Anyway, thank you folks. :)

---

