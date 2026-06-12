---
title: "Would like to have persistent name of a windows drive"
date: 2008-11-28
forum: General Help
---

### Post by dfro on 2008-11-28
When I boot into Ubuntu, it recognizes a Windows drive that I have in the computer. It calls it "125.0 GB Media". When I click on it in the desktop window, it mounts and I can navigate through the directories, which is great. If I run the command "mount", it shows that the drive is located here:

/dev/sdb1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

Can I have Ubuntu give it a name other than "125.0 GB Media" - like "Windows_XP"?

Can I do this without altering the Windows drive at all?

It is a little thing, but I learned how to label external usb hd's using e2label, and it would be great to get all the drives named.

Thanks,
dfro

---

### Post by scouser73 on 2008-11-28
This should help you; [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by cariboo on 2008-11-28
Install ntfsprogs, it is in the repository, then use ntfslabel to create a label for your ntfs partition.

You can also use Windows disk management tools to create a label.

Jim

---

