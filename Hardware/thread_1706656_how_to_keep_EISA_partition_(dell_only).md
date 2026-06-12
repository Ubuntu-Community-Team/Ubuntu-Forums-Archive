---
title: "how to keep EISA partition (dell only?)"
date: 2011-03-14
forum: Hardware
---

### Post by charileb000 on 2011-03-14
I have a Dell 1737 and it had a:  150Mb EISA partition  20GB windows restore partition and the rest of the 500GB,was for windows kista.    and that leaves only one partition for linux, i dont think the windows boot loader would boot linux from an extended (it had plenty of ram 4GB but i still did want a swapper, and a another NTFS partition incase the other goes bad - been caught out too much). so i backed up the EISA using UBCD (a tool on it - the last one in the backup list) and deleted the partition (but didnt overwrite it), created an extended partition with a data partition and a swap in side it (in that order) and the linux partiton on the end.   after installing UB, the Diagnostics option in the boot screen still works (so its somehow accessing the former partition)!. the backup of the EISA, compressed to just over 3mb, formally 8mb, and i put that on the windows recovery partition (along with a backup of vistas equivilent of bootini). and grub boots vista fine, its oddly called Windows Recovery Environment...  im not sure if this will work so well for others, but just letting you know that it &quot;could be&quot; safe to remove the EISA partition and still use the diagnostic programs on it.  CB

---

