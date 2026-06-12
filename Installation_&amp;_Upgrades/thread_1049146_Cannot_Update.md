---
title: "Cannot Update"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by renlux on 2009-01-24
I tried to update using the update manager and I got these messages:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://ph.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

What do I need to do?

---

### Post by lemming465 on 2009-01-25
In a terminal window try```

sudo -i
apt-get clean
apt-get update
apt-get upgrade
```
Does that improve things any?

---

### Post by SOULRiDER on 2009-01-26
Check this out
[http://ubuntuforums.org/showthread.php?t=1031404&highlight=40976EAF437D05B5&page=2](http://ubuntuforums.org/showthread.php?t=1031404&highlight=40976EAF437D05B5&page=2)

---

