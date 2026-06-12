---
title: "how can i get write permission to my usb hdd?"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by martinez9049 on 2005-10-05
i can read and execute just fine, but it won't let me write to it b/c it says it's a read-only disk.

thanks,
ismael m

---

### Post by Curlydave on 2005-10-05
What's the drive's format? If it's NTFS, that's your problem.

---

### Post by mlomker on 2005-10-05
If it's vfat then you can [add a line]("http://ubuntuforums.org/showpost.php?p=355988&postcount=8") to your fstab file.  As curlydave stated, NTFS drives are read-only in Ubuntu.

---

### Post by martinez9049 on 2005-10-05
im pretty sure it's fat32...is there a way of checking this?

---

### Post by mlomker on 2005-10-05
> im pretty sure it's fat32...is there a way of checking this?

If it is mounted then the **mount** command will tell you.

```

root@mlomkernote:/ # mount
/dev/hda1 on / type **reiserfs** (rw,notail)

```

---

### Post by martinez9049 on 2005-10-05
ok, nevermind...it's ntfs. for some reason i could've swore i made it fat32. thanks though

---

