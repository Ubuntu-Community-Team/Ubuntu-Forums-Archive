---
title: "Another issue with software sources"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by daithi_dearg on 2009-08-20
Hello,

Similar to link:
[http://ubuntuforums.org/showthread.php?t=1135432&highlight=update+manager](http://ubuntuforums.org/showthread.php?t=1135432&highlight=update+manager)

I try to run apt-get update and following errors are seen:
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

apt-key update gives following errors:
root@eireanngobreagh:~# sudo apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2

apt-get update still fails with same errors.

Any suggestions?

---

