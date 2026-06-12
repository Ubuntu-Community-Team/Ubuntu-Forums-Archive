---
title: "[SOLVED] On-the-fly encryption"
date: 2008-09-13
forum: General Help
---

### Post by Linux user 66 on 2008-09-13
In Windows I used AxCrypt for on-the-fly file encryption. What program (apart from TrueCrypt and KeePass) is recommendable for on-the-fly file encryption/decryption in Ubuntu?

---

### Post by javaJake on 2008-09-13
There are two options. You can either encrypt a directory, or encrypt an entire partition:

[LIST]
[*]**Directory:** [http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)
[*]**Partition:** [https://help.ubuntu.com/community/EncryptedFilesystemHowto7](https://help.ubuntu.com/community/EncryptedFilesystemHowto7)
[/LIST]

I wasn't able to test the partition method, but the directory method worked fine for me.

The only thing to note about the directory method is, on step 5, when it asks...
```
Creating new encrypted volume.
Please choose from one of the following options:
 enter "x" for expert configuration mode,
 enter "p" for pre-configured paranoia mode,
 anything else, or an empty line will select standard mode.
?> 
```
...just hit ENTER for the default mode and continue.

---

### Post by Linux user 66 on 2008-09-13
> **javaJake said:**
> There are two options. You can either encrypt a directory, or encrypt an entire partition:

[LIST]
[*]**Directory:** [http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)
[*]**Partition:** [https://help.ubuntu.com/community/EncryptedFilesystemHowto7](https://help.ubuntu.com/community/EncryptedFilesystemHowto7)
[/LIST]

I wasn't able to test the partition method, but the directory method worked fine for me.

The only thing to note about the directory method is, on step 5, when it asks...
```
Creating new encrypted volume.
Please choose from one of the following options:
 enter "x" for expert configuration mode,
 enter "p" for pre-configured paranoia mode,
 anything else, or an empty line will select standard mode.
?> 
```
...just hit ENTER for the default mode and continue.

Thanks!

---

