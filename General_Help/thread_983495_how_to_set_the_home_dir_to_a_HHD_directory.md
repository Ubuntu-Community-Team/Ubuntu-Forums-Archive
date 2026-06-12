---
title: "how to set the home dir to a HHD directory"
date: 2008-11-15
forum: General Help
---

### Post by wildbat on 2008-11-15
how to set the home dir to a Host HD directory like have the /home mount to C:\Documents and Settings\user\

---

### Post by Yownanymous on 2008-11-16
I don't think that's possible due to the fact that:
a)Ubuntu is on a virtual disk image with wubi.
b)Ubuntu and Linux systems use a completely different file and storage system, I think it's called ext3 (someone correct me if I'm wrong) whereas modern editions of Windows use NTFS and older ones use FAT32.

---

### Post by vanadium on 2008-11-16
I fully agree with Yownanymous. Your home directories should remain on the Ubuntu volume. However, you can store all your user data on the Windows partition. It is perfectly possible to create symbolic links within your home directory to your Windows directory (e.g. a symbolic link "Documents" to "Documents and Settings/ ... / My Documents" on your Windows volume, another symbolic link "Music", etc.) such that all your user data reside on the Windows volume, but are directly within reach from within your Ubuntu home directory.

---

