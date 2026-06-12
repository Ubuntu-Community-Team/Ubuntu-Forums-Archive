---
title: "External Hard Drive Permissions"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by deville75 on 2007-03-01
I have an external hard drive and I have almost all my video, music, documents, and etc on it.  I used to use it on XP and now since I use UBUNTU more often I use it on LINUX.  Anyway, I'm able to read all the data, play videos, play music, but I can't change any documents, or copy any videos to the harddrive.  I checked the permissions and it has Read and Execute checked.  So I tried to check mark Write option, but it won't let me.  How can I change this? Do I log in as admin? How do I log in as admin?

---

### Post by taurus on 2007-03-01
Run this from a terminal or <Alt>F2.

```
gksudo nautilus
```

---

### Post by UltraMathMan on 2007-03-01
If you used to use the drive in Windows, my bet is that it's formatted with an NTFS filesystem. NTFS cannot be read natively in Ubuntu, as Microsoft seems reluctant to give up the details that would make it easy. [This thread]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs") might interest you and provide a solution.

-Hope this helps :)

---

### Post by deville75 on 2007-03-02
> **taurus said:**
> Run this from a terminal or <Alt>F2.

```
gksudo nautilus
```

What does this do? It opened an explorer, but I still couldn't copy it to the external hard drive.

---

### Post by deville75 on 2007-03-02
> **UltraMathMan said:**
> If you used to use the drive in Windows, my bet is that it's formatted with an NTFS filesystem. NTFS cannot be read natively in Ubuntu, as Microsoft seems reluctant to give up the details that would make it easy. [This thread]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs") might interest you and provide a solution.

-Hope this helps :)

Well I'm able to read the external perfectly fine.  The only problem I have is writing, which is due to permissions.  Can I change the permissions for my user for that drive?  Maybe if I could log in as admin was what I was thinking. But I don't kno how to do that.

---

### Post by Mr. C. on 2007-03-02
> **UltraMathMan said:**
> If you used to use the drive in Windows, my bet is that it's formatted with an NTFS filesystem. NTFS cannot be read natively in Ubuntu, as Microsoft seems reluctant to give up the details that would make it easy. [This thread]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs") might interest you and provide a solution.

-Hope this helps :)

This is incorrect.  NTFS reading in linux systems has been around for years.  Its the writing part that has been troublesome.  There have been recent advances, but they are not perfect yet.

Consider NTFS read-only for now.

MrC

---

### Post by UltraMathMan on 2007-03-02
Whoops, I must have been a little too eager to answer :oops:. I meant to say native NTFS *writing* isn't supported, the same link should apply though as a means of getting around this. Sorry about that.

---

