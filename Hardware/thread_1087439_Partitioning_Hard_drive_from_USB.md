---
title: "Partitioning Hard drive from USB"
date: 2009-03-05
forum: Hardware
---

### Post by Redenbacher on 2009-03-05
I've been trying to partition the hard drive on my HP mini via USB Flash drive.

The reason being, I would like to dual-boot Ubuntu on my 1035NR.

I've tried creating a LiveUSB through 8.10 on my desktop, but the install utility would not read that I had windows installed, and wanted to wipe the whole hard drive and replace it with Ubuntu!

Not an option. What happened to the little slider for resizing the partition that the old ubuntu installer used to have...?

Anyway, I decided I would use a separate partitioner first. Naturally, I chose Gparted. The GParted documentation on creating a liveUSB was a bit difficult to follow, so I used UNetbootin to create a liveUSB from the .iso. 

It booted up, but I get the error message "Could not find kernel image: gparted"

So then I used UNetbootin to create a LiveUSB of Partition Magic. Well that would get me to choosing a video code, and then would lock up and not proceed any farther.

I even tried the GParted LiveUSB on my desktop to see if perhaps it was my Mini that was causing the problem, but I received the same error on there. So that lead me to believe it was UNetbootin causing the issue.

I found a HOWTO on here, ubuntuforums, for making a GParted LiveUSB with Ubuntu, by mounting the LiveCD, copying the files to the USB, and installing syslinux. When I tried to boot that up, I received an error that said there was no bootable partition.

So I'm out of ideas, and I was hoping the community could help. I thank you in advance for any suggestions :).

---

### Post by Redenbacher on 2009-03-05
Bump

---

### Post by Redenbacher on 2009-03-07
Bump

---

### Post by Redenbacher on 2009-03-07
Bump!

---

### Post by Redenbacher on 2009-03-08
Bump!?

---

### Post by Redenbacher on 2009-03-09
Well, I know you all have been *very* eager to help me. However I did manage to figure it out.

Before you boot in to a live session of Ubuntu to begin partition editing and installation, use Windows to fix up your harddrive, this will take a bit.

    1. Go to Start -> My Computer -> Right-click C: (or whatever the HDD in question is titled)
    2. In the pulldown, click Properties, then navigate to the Tools tab.
    3. Do a disk clean up, followed by a defragmentation. 
    4. Then go to Check Disk for Errors, tick the two boxes that appear.
    5. A dialog box will pop up that says you can not do it here, and would you like to schedule a disk check the next time you reboot, click Yes.
    6. Reboot your machine, and allow the check to run its course. It took my 60GB HDD an hour or better.
    7. It will reboot automatically when it is done, boot in to windows again, otherwise GParted will give you an error about Windows not being shut down cleanly.
    8. No reboot in to your Live Session
    9. Go to System -> Administration -> Partition Editor (This is GParted)
    10. Your NTFS Partition should now be resizeable. 

Make sure if you plan to partition with GParted, the package *ntfsprogs* must be installed. You can do so by searching for it in Synaptic Package Manager.

---

