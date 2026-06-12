---
title: "update repository errors"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by pjhudson on 2009-03-13
I tried to update using the update manager and it comes back with the following errors:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  

W: Failed to fetch [http://th.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://th.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


I'm in Thailand, and pretty new and don't know how to change the repository urls --  they were working fine a few months ago.

---

### Post by taurus on 2009-03-13
Go into System -> Administration -> Software Sources and try another server.  Make sure you close down update manager first though.

---

### Post by pjhudson on 2009-03-13
awesome-- thanks for replying so quickly- I guess need to go through a crash course on how to use linux--

---

