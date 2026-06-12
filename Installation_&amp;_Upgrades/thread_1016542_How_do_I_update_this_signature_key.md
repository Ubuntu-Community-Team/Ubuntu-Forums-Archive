---
title: "How do I update this signature key?"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by selahlynch on 2008-12-20
I got the following error from Synaptic after clicking "reload" (similar to "apt-get update")

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

From a bit of research, I understand that I need to download and import a new signature key in order to verify the signature of this archive.

But how do I do this?  
Is there a keyring package I can install with apt or synaptic?  
Or, maybe I must use gpg --recv-keys to retrieve a key.  If so, what is my keyserver?
Any other suggestions?

---

### Post by selahlynch on 2008-12-20
I found couple of other potential methods, but no luck yet.  

I downloaded the file 'http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg'.  Is this even the proper key file??

Then on my Gnome (2.22.3) desktop I tried: 
System-->Administration-->Software_Sources
Authentication-->Import_Key_File
I selected Release.gpg and pressed OK, but no new key showed up in the Authentication window. 

I also tried:
$ apt-key add Release.gpg
gpg: no valid OpenPGP data found.

And I checked, but I still get the same signature verification error when trying to refresh/update in Synaptic.

---

### Post by selahlynch on 2009-01-03
bump...
can anyone help me update my signature key so that I no longer get the following error:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

