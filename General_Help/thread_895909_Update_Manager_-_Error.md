---
title: "Update Manager - Error"
date: 2008-08-20
forum: General Help
---

### Post by yusy86 on 2008-08-20
hi everybody..

every time i run Update Manager the following error appear:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://bh.archive.ubuntu.com](http://bh.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://bh.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://bh.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


what's the problem here???

---

### Post by fedex1993 on 2008-08-20
Sounds like if you added a seprarate repo you forgot to acpt the gpg key.

---

### Post by gpmiii on 2008-08-21
> **fedex1993 said:**
> Sounds like if you added a seprarate repo you forgot to acpt the gpg key.

I'm having the same issue; so what is "acpt the gpg key" and what must be done to resolve it?

Thanks - g

---

### Post by gpmiii on 2008-08-21
That's okay, figured it out... worked for me anyway.

Open System menu, Administration, Software Sources.
Choose "Other" from the "Download From" List and choose the "Best Server".

This will run some tests to get you the optimal server for updates and will rewrite your /etc/apt/sources.list

Then run Update Manager as before

---

