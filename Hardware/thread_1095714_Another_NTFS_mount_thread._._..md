---
title: "Another NTFS mount thread. . ."
date: 2009-03-14
forum: Hardware
---

### Post by Tamnakz on 2009-03-14
I've recently installed Ubuntu 8.10 with all available updates to a Dell XPS M1210.

I'm trying to use my WD Passport 320g external HD.

When plugged in, I get the same error I've seen several times while trying to find info on fixing it: 
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use.

I don't have an available windows OS to connect and properly disconnect this device.

I cannot get the 'force' option to work.

Several questions:

-I assume the NTFS lists itself as in use/not in use. When disconnecting it from a Windows OS, it stays 'in use' but Windows will re-mount anyways. Is this assumption correct?
-Once I get this drive to mount properly, will it continue to do so with Ubuntu? What if I use it on Windows again, it'll work so long as I disconnect properly?

There's a second part of the mount option in the error, it reads:
Or add the option to the relevant row in the /etc/fstab file:   /dev/sdbi/media/tamnaz ext ntfs-3g force 0 0

It does not give any further explanation, what does this command do?
Will doing this solve the problem long term?

Thanks in advance for any help!
   Nick

---

### Post by arsenic23 on 2009-03-14
You might be typing the force option incorrectly, just to make sure, are you typing something like:

```
sudo mount /dev/sdb1 /folder/with/correct/permissions -o force
```

---

