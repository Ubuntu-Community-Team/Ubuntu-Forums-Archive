---
title: "WD NTFS External Drive Forces Files to be Executable"
date: 2010-08-08
forum: Hardware
---

### Post by Dylnuge on 2010-08-08
EDIT:

I tried another NTFS drive and noticed the same problem I described below, so I'm pretty sure this is related to the default NTFS support in Ubuntu and was wondering if anyone could help regarding that, since I can't find a lot about NTFS in Ubuntu that appears to be recent.

Every file/folder/etc on an NTFS drive read from Ubuntu appears to have full read/write/execute permissions for owner, group, and others with no ability to change it (not an error message--rather, after making the change it appears to revert).

The real issue I have with this is the executable bit part--files that are not and should not be read as executable are.

I am trying to transfer files from an old computer to a new computer, and I don't want to wind up with all my files being executables. Further, I need to be using this drive for both Windows and Linux, which means that I can't reformat to ext4. I would prefer not to use FAT32 if at all possible, due to the limitations inherent in the file system.

Does anyone know if there is default NTFS support in Ubuntu (I can't find any documentation on it, though I might be looking in the wrong place) and if so, whether or not this is a reparable issue. For reference, both my new and old computer are having this problem, it is with both files already on the drive (ones it is only trying to read) and files created in Ubuntu, and it does not appear to have anything to do with the make/settings of the external drive, contrary to my original suspicions.

Thanks!

==Original Post==
I recently got a new computer and purchased with it an external drive, with the hopes that in addition to using the external drive to store more files I could copy my files from my old laptop to my new one without incident.

The drive (A Western Digital My Book) works fine in Windows, and at first appeared to work fine for both read and write access in Ubuntu.

The issue is that any file, regardless of type or content and regardless of whether it was created on the drive or copied over, forces itself to have read permissions set to 777 (read/write/execute privilege for all users).

I would like to avoid having to format the drive to FAT32 (as I personally dislike said filesystem; I would prefer a journaled system like ext4 on the drive but since it must communicate with both Linux and Windows I am well aware that this is an impossibility). Does anyone else use this or a similar WD drive or have a similar issue, and if so, does anyone know how to resolve it?

Thanks!

---

### Post by Dylnuge on 2010-08-14
Does anyone have any experience with forced permissions on a drive like this situation? I'm trying to transfer to a new computer and my concern is that if I copy paste the drive contents from one to the external drive to the other, the new computer won't be able to handle the files due to them all being marked executable.

Since I need to use both Windows and Linux and only have one external drive, I was hoping to be able to work with it under standard formatting, especially since I have had success in the past working with NTFS partitions under Linux. However, a locked executable bit would make it impossible to use or interact with the drive and its contents under Linux.

---

