---
title: "Cannot be installed on computer type."
date: 2008-10-17
forum: General Help
---

### Post by Goda on 2008-10-17
I just installed Ubuntu 8.04 for a friend and the Add/Remove Programs menu says software "cannot be installed on your computer type(i386)". I installed with the i386 CD. He has a Dell Inspiron 8600, with a Pentium M processor.

---

### Post by WSmart on 2008-10-17
Have you tried the alternative CD?  That's the sure fire way to do an install.  It's recommended for all non-standard or legacy installs, I believe.  

It can also do upgrades, as an aside.  You can get the alternative CD via torrent and save the community some server traffic.

---

### Post by Goda on 2008-10-17
The system itself is installed. It just can't install from the Repository.

---

### Post by jespdj on 2008-10-17
Here is something you could try. Open a terminal and type:
```
sudo apt-get update
```
This will update the list of packages from the Ubuntu repository. I've noticed sometimes that this is necessary on a freshly installed Ubuntu.

---

### Post by Goda on 2008-10-17
I'm getting an error message.

> W: A error occurred during the signature verification. The repository
is not updated and the previous index files will be used.GPG error:
[http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following
signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive
Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release: The
following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu
Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The
following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu
Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch
[http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)

W: Some index files failed to download, they have been ignored, or old
ones used instead.

And I just realized that I'm getting it too when I update. We're both on a the same university network, is it possible that that is the problem?

---

### Post by Ryadt on 2008-10-17
It might be that there is a problem with the server you are trying to download from.
Go in Software Sources and from the 'Download from' drop-list, select 'other' and then choose 'Select Best Server.
Then run an update.

---

