---
title: "Vista won't boot after filesystem move..."
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by Keatonguy on 2009-08-10
I'm working on a brand new Acer Aspire 6920, installing Ubuntu alongside Vista. The system was set up with the drive partitioned in half already, out of the box, but the Vista partition was in the middle of the drive. So, I deleted the empty partitions around it and did a filesystem move to put the Vista partition at the start of the drive. It seems to have worked properly, I can mount it in Linux and all the files are there, but it said that the move failed once it was done, and when I try to boot into Vista in the GRUB menu, it just restarts back at the BIOS. For the record, both systems are 64-bit. 

Has anyone seen anything like this, or have any suggestions how to figure out what's wrong?

---

### Post by abrari on 2009-08-10
Please post your boot.ini file (that's on Vista's root directory).
Try to edit the line to something like: multi(0)disk(0)partition(0).

---

### Post by Keatonguy on 2009-08-10
Err... There isn't one. Unless it's supposed to be under C:\Windows?

---

### Post by Keatonguy on 2009-08-10
Correction: There is no boot.ini in Windows Vista. They replaced it with a big heap of files in the BOOT directory, which I have no experience fiddling with.

So, I reiterate my plea: Help!

---

### Post by Tclarkie on 2009-08-10
do you really feal so bad losing "Vista"

---

### Post by Keatonguy on 2009-08-10
Thank you very much for the constructive comment.

---

### Post by Tclarkie on 2009-08-10
sorry, now heres the real help
ubuntuforums.org/archive/index.php/t-956399.html

---

### Post by Keatonguy on 2009-08-10
Hrmm... Thanks for the help, but unfortunately this isn't the issue. GRUB comes up fine and lists everything, but when I try to boot Vista, even through the Super Grub Disk, or even by removing GRUB altogether and letting the BIOS try to go through the Windows bootloader, it just shuts off and returns to the BIOS, like it's in a loop.

Honestly, I've never seen anything like this, and it's really annoying. This laptop is brand new, but it didn't come with any recovery discs. It was all in a hidden partition I deleted when I was installing Linux, so I'm really up **** creek without a paddle. =/

Still hoping for advice, so if anyone out there has any ideas, or maybe even better can point me to a good resource for info on fixing Windows, leave a post.

---

### Post by Mark Phelps on 2009-08-10
How did you "move" the Vista partition?  Did you use some third-party commercial product like Acronis Disk Director or one of the Paragon products? Did you use the built-in Vista Disk Management utility? Or did you use the Ububuntu installer or Linux GParted utility?

The answer affects what you will need to use to "fix" it.

---

### Post by gabry79Italy on 2009-08-10
try these below:

sudo apt-get install ntfsprogs
umount vista partition (for example with gparted, or if you know vista partition on dev with this: sudo umount /dev/sdx where x is vista-partition)
run in terminal:
sudo fsck -y /dev/sdx     (if you don't know x post me back output of this code: sudo fdisk -l)

---

### Post by Mark Phelps on 2009-08-10
> **gabry79Italy said:**
> sudo apt-get install ntfsprogs

ntfsprogs includes ntfsfix -- which is NOT a Linux version of CHKDSK.  All it will do is mark the partition as needing to run CHKDSK the next time you reboot it.  It can not be used to do in-depth repair of NTFS volumes.  Even the Man page makes that clear.

> sudo fsck -y /dev/sdx
This is an NTFS volume, not Ext3/4.  Fsck can't be run against NTFS volumes.

---

### Post by Keatonguy on 2009-08-10
> **Mark Phelps said:**
> How did you "move" the Vista partition?  Did you use some third-party commercial product like Acronis Disk Director or one of the Paragon products? Did you use the built-in Vista Disk Management utility? Or did you use the Ububuntu installer or Linux GParted utility?

The answer affects what you will need to use to "fix" it.

I used the partition manager on the Ubuntu live CD. Vista was on sda2, which I moved to the front of the drive in order to merge my unformatted space.

Also, I did try both fsck and ntfsfix as you folks suggested, no dice I'm afraid.

Currently, I'm getting my hands on a copy of the same version of Vista that's on this machine (Home Premium 64-bit) in order to use the repair functions on it. With any luck, that might salvage the installation.

Thanks for all the help, everyone, I appreciate it. I'll post back after I try this.

---

### Post by Mark Phelps on 2009-08-10
> **Keatonguy said:**
> I used the partition manager on the Ubuntu live CD. Vista was on sda2, which I moved to the front of the drive in order to merge my unformatted space.

Well ... I've been posting time after time about NOT using Ubuntu utilities to mess with the Vista OS partition because doing so, causes exactly the kinds of problems you've experienced.

You could have done the same with the Vista Disk Management utility -- and you wouldn't have been risking OS corruption as a side effect.

However, if you can lay your hands on a Vista DVD, you can try booting from it and running Startup Repair.  It doesn't have to be the same version; the repair function is the same on all the DVDs. You will probably have to do that several times.

---

