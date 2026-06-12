---
title: "Why won't it update???"
date: 2008-09-16
forum: Hardware
---

### Post by doctorbrowder on 2008-09-16
For several weeks now, Ubuntu has refused to update. Every time I run the sudo apt-get update command, this is what I get:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://om.archive.ubuntu.com](http://om.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://om.archive.ubuntu.com/ubuntu/...pdates/Release](http://om.archive.ubuntu.com/ubuntu/...pdates/Release)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

How do I get around this eternal error and force Ubuntu to update??? Thx

---

### Post by DoctorMO on 2008-09-17
Go to System > Administration > Software Sources

Then in the dropdown "Download From" make sure that you've got a valid and correct mirror set up.

If that is the case then you need to remove a custom apt server listing in /etc/apt/source.list.d/*.list or /etc/apt/sources.list make sure you don't delete the main ubuntu repositories.

Good luck.

---

### Post by jantra on 2008-09-17
Also check with your ISP.

---

### Post by jantra on 2008-10-02
Hi,

If you have got the solution, then please post it here so that others can also get the benefit of your experience.

Thanks.

---

