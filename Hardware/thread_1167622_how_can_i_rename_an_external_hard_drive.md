---
title: "how can i rename an external hard drive??"
date: 2009-05-23
forum: Hardware
---

### Post by Ichindar on 2009-05-23
hi all

ive just purchased a maxtor 1 TB external hard drive, im planning on buying another soon and i would like to rename them HD 1 and HD 2, but i have no idea how to change the names of them?

i tried to right click and rename but it said not supported by the back end??


any help is appreciated.

---

### Post by mikewhatever on 2009-05-23
Check out the guide. [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by Ichindar on 2009-05-23
thanks for the reply, i tried the gparted program, but the "label" button is blanked out, i cant use it, any other ideas?

---

### Post by lindsay7 on 2009-05-23
I Gparted, right click the drive or partition and unmount it. Then you can change the label or name.

---

### Post by mikewhatever on 2009-05-23
> **Ichindar said:**
> thanks for the reply, i tried the gparted program, but the "label" button is blanked out, i cant use it, any other ideas?

You probably need to use the NTFS tool, since the filesystem is probably NTFS. It's unlikely Maxtor will sell ext formatted HDDs. Gparted should work with any linux file system as well as FAT32.

---

### Post by Ichindar on 2009-05-23
your a champion! that worked, thanks for your help, much appreciated

---

