---
title: "Software Sources Error"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by derekbuc on 2009-04-24
Somethings wrong with update-manager so i ran apt-get update and it returned this.

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/Release](http://archive.canonical.com/ubuntu/dists/intrepid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

---

### Post by derekbuc on 2009-04-24
I found a post where someone suggested this command.
sudo gpg --keyserver hkp://subkeys.pgp.net --recv-key 437D05B5
But that didn't work. It returned this.

gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

I'm sure its a new version of that key i need or something like that. How or where do I download it from?

---

### Post by derekbuc on 2009-08-20
Still not working lads
bump

---

### Post by oldos2er on 2009-08-20
Have you tried **sudo apt-key update** ?

---

