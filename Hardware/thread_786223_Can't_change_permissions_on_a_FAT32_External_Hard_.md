---
title: "Can't change permissions on a FAT32 External Hard Drive"
date: 2008-05-07
forum: Hardware
---

### Post by Garrulousbrevity on 2008-05-07
So, I have a 500GB Western Digital My Book external, with a FAT32 file system.  I can read and write to it without a problem, but I would like it so that other users could access it without unmounting it and mounting it again.  

When I go to /media/ and click on preferences, it clearly states that my user is the owner, and that no one else has privileges.  If I try and give "Others" the ability to Create and Delete files, the drop down windows stays that way for about a tenth of a second and then switches back to "None." 

Is there a set of terminal commands I could use to change permissions?  

Also I wanted to change the name of the drive.  Finding no easy way with Nautilus, I decided to borrow a windows PC and do it, and now the name is in all caps.  I'll live with it, but is there a way to have... not... caps...? 

Thanks in advance.

---

### Post by tomchuk on 2008-05-08
Fat 32 doesn't support permissions in any way, shape or form. The only thing you can do is mount with the uid, gid, umask, fmask and dmask options, to limit or grant permissions to a certain user or group. If you wanted to give all users in the 'users' group read and write access, you'd mount with gid=100,umask=002. man mount and check out the "Mount options for fat" section.

---

### Post by Garrulousbrevity on 2008-05-08
Ah.  That makes more sense now.  

In the long term, would it be easier to just copy everything over, change the file system and copy it back?

Which file system would be easier? 

Is there a simple enough way to change the file system? 

Thanks.

---

### Post by DocBob on 2008-05-08
> **Garrulousbrevity said:**
> Ah.  That makes more sense now.  

In the long term, would it be easier to just copy everything over, change the file system and copy it back?

Which file system would be easier? 

Is there a simple enough way to change the file system? 

Thanks.

I know there's a way to convert the drive from FAT to NTFS in Windows. I'm not sure how it would be done with Ubuntu but, i'm sure there's a way. I'd investigate.

---

### Post by tomchuk on 2008-05-08
If finer grained control over permissions and ownership is important to you and if you're only ever going to be connecting the drive to a Linux machine, Just copy everything off, format the drive ext3 and copy everything back, it'll work out much better.

---

### Post by tomchuk on 2008-05-08
> **DocBob said:**
> I know there's a way to convert the drive from FAT to NTFS in Windows. I'm not sure how it would be done with Ubuntu but, i'm sure there's a way. I'd investigate.

If you've got the drive space to spare on other drives, I wouldn't even mess with trying a conversion, even if it were available. Even on Windows, MS strongly advises backing up your data before converting Fat32 to NTFS.

---

### Post by Garrulousbrevity on 2008-05-08
Well, bewtween my laptop, my desktop, and my girlfriend's laptop, I do have enough space to back everything up.  I'm most of the way through doing so already.  To switch to ext3 (because the hard drive is always attached to my Desktop, and whe other people want files off there they have always used SSH to grab them anyway) do I just go into the partition editor and fool around?  Or is there a commandline way to do it?  I haven't reformated a hard drive while not installing Ubuntu before.

---

### Post by Garrulousbrevity on 2008-05-08
Hey, just finished transferring everything back to the external, and everything seems to be working fine.  

Thanks for the help.

---

