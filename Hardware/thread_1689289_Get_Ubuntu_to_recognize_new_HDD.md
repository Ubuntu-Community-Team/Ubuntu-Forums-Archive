---
title: "Get Ubuntu to recognize new HDD?"
date: 2011-02-16
forum: Hardware
---

### Post by javyn999 on 2011-02-16
Hey all.   Last night I installed and formatted a new 2 TB (Hitachi Deskstar 5900 rpm, 512b sector) to use as a data drive for my dual boot Windows 7 64 and Ubuntu 10.04 machine.

I formatted the drive in Windows, ntfs....but when I boot into Ubuntu it does not see the drive.

How may I set it up to where Ubuntu can access this drive too?

Thanks.

---

### Post by quadproc on 2011-02-16
> **javyn999 said:**
> 
I formatted the drive in Windows, ntfs....but when I boot into Ubuntu it does not see the drive.

Did you add the new partition(s) into your fstab?  If not then the system will not automatically mount the drive at startup time.

You can see what is mounted at any time by typing in
```
mount
```in a terminal.  Such drives usually show up at the end of the list.

If you want to manually mount the drive then you have some choices.  You can use System>Administration>Disk Utility, select the drive of interest, and push the mount button.  Or, if you would rather mount it with a name of your own choosing, first create a directory entry where the new drive will reside:
```
sudo mkdir /[COLOR=Red]newdrive[/COLOR]
```Then mount it using something like
```
sudo mount -t ntfs /dev/[COLOR=Red]sdb1[/COLOR] /[COLOR=Red]newdrive[/COLOR]
```Of course, substitute your actual desired directory name for newdrive.  Substitute the desired partition name for sdb1.

You will also need to umount the drive before you do anything like power down or disconnect the drive.

quadproc

---

