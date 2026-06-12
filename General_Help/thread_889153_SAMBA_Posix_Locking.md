---
title: "SAMBA Posix Locking"
date: 2008-08-13
forum: General Help
---

### Post by raywood on 2008-08-13
I've got a problem using MS Word in VMware on a Hardy host.  It is a matter of being unable to save files.  Others have linked this to the "posix locking" setting in the SAMBA configuration file.  See e.g., [http://fixunix.com/samba/489288-samba-xp-sp3-posix-locking.html]("http://fixunix.com/samba/489288-samba-xp-sp3-posix-locking.html")

A solution that some have recommended is to set posix locking = no.  Unfortunately, I cannot find the SAMBA configuration file that contains a posix locking option.  I have searched my filesystem for smb.conf and have found four files, none of which contains that option.

My questions:

(1) Is there some other approach I should be using instead?

(2) Where can I find the configuration file that does contain a posix locking option?

TIA ...

---

### Post by raywood on 2008-08-25
I have found a workaround.  Microsoft Word running in VMware cannot save files, on my computer, on an NTFS partition.  It can do so, however, on an ext3 partition.  I have not checked whether it can also do so on a FAT32 partition.

---

