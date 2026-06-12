---
title: "Mounting the un-mountable"
date: 2023-07-30
forum: Hardware
---

### Post by Langstracht on 2023-07-30
I think the 'not mounting' situation was caused by the external HD losing power during a back up with "back in time".  

In any event, the drive now refuses to mount.  

Given the contents of the drive this is a bit of a disaster.

Anyone have any ideas how to rectify this situation?

Assistance GREATLY appreciated.

---

### Post by ajgreeny on 2023-07-30
Tell us more about this drive.

Is it a spinning disk HDD or a solid state SSD; internal or external?
What filesystem is it formatted to, a Linux filesystem such as ext4 or a Microsoft Windows filesystem such as NTFS?
Have you tried mounting it using a terminal command? If so what error did the terminal show?

If you have a Windows computer available and can attach the drive to that you may find it will now mount if it is formatted to NTFS, though it may need to run chkdisk first to repair any filesystem faults.

---

### Post by Langstracht on 2023-07-30
The HD is external "spinning".

It is (unfortunately I think) formatted to NTFS.

Since no software identifies the drive (it not being mounted/mountable) I have not been able to "CLI mount".

I do not have access to a Windows machine.

---

### Post by Langstracht on 2023-07-30
Interesting - (close to) Windows got replaced by **********

---

### Post by ajgreeny on 2023-07-30
As it is an external drive perhaps you know someone who will let you attach it to their Windows machine and use chkdisk on it.

That may be all that is needed to repair the filesystem following the power-off while it was still mounted and unfortunately Linux has nothing in its own armoury that you can use to do this.

As an aside, NTFS is not a useful filesystem to use in Linux if you do not either dual boot or have another computer running Windows that you can use for this repair.

---

### Post by ajgreeny on 2023-07-30
> **Langstracht said:**
> Interesting - (close to) Windows got replaced by **********
That will be the result of our forum software noting that you had used an alternative spelling of Windows that has been listed by moderators and administrators of this forum as unacceptable according to the forum rules which you can view at [https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules) and say > Attacks and derogatory terms of any kind are not welcome. This includes references to any operating systems or the companies that produce them..
I am unable to see what you originally wrote but can only assume it was pejorative in some manner. Please do not use such terms or spellings in future.

---

### Post by Langstracht on 2023-07-30
You seem to be saying that my only (potential) fix is access to a Windows computer.

Is that correct?

If so, that's a pretty sad indictment of Linux capabilities.  And an added impetus to not saying anything even slightly pejorative about Windows ...

---

### Post by ajgreeny on 2023-07-30
Yes, unfortunately you're correct!

There are a number of utilities that can help repair NTFS to some extent but NTFS is a proprietary filesystem owned by Microsoft and Linux developers can only do their best as they can not see source code in order to create a full chkdisk replacement for us.

---

### Post by yancek on 2023-07-31
>  If so, that's a pretty sad indictment of Linux capabilities

No, it isn't.  The reason it is the case is explained in post 5.  Bear in mind that a vast number of servers world wide run on Linux yet default microsoft systems can not even read a Linux filesystem much less write to it and/or make repairs.  This is a choice made by microsoft.  If you do not have windows, there is no reason to use a windows filesystem.

---

### Post by notlim_hardy on 2023-07-31
It refuses to mount. Does it at least have power? If it doesn't, not even a Windows machine will do.

---

### Post by TheFu on 2023-08-01
Back In Time doesn't work with NTFS.  It requires a native Linux file system, like ext4. Using NTFS, it is unlikely all those backup version will be restored correctly.  Back-in-time is like all rsync+hardlink backup options. They need the file system to maintain users, groups, ACLs, xattrs along with supporting hardlinks to work correctly.  Last time I looked, NTFS doesn't.

I suppose you've never restored anything except little data files from these "backups"?

Also, if I have to have a drive fail, the best drive to have that happen on is the drive holding backups, not primary data!  Count yourself lucky.  After all, backup drives hold the 2nd or 3rd copy of data, not the primary copy.

Some needs to say this. You made a poor choice with NTFS, if that truly is the file system, to store your backup data using Linux.  A few Linux backup tools can store their data to any sort of file system because they embed the file metadata into their backup data chunks. If you need that, then check out backup tools based on Duplicity.  However, be certain you research about backup failures for any backup tool BEFORE choosing. This way, you'll have a better chance of picking the best option for your needs and skills.

Any file system driver that doesn't have the development team sharing the source code with the world, freely, is not going to be the best choice for Linux.  NTFS is a proprietary file system. MSFT changes it from time to time.  The break things and don't tell anyone in the Linux community about their breakage.  If you plan to use Linux, using NTFS should be lower on the list of choices until MSFT decides that working with others is in their interest.  Heck, MSFT could port almost all the native Linux file systems to MS-Windows, if they liked. After all, most are released under the BSD or GPL licenses, so the source code would be just as available to MSFT as it is to you and I.  Blaming Linux for MSFT's legal issues doesn't make sense.  Proprietary software licensed ARE legal issues.

We each have a choice.  Live and learn.

---

