---
title: "Failed to download some Release or Release.gpg files!"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by Lars Noodén on 2009-04-18
Debmirror runs into some kind of obtacle to making a mirror with gpgv.
What's a solution?

I seem to have the keys:

$ gpg --keyserver pgpkeys.mit.edu --recv-key 437D05B5
gpg: requesting key 437D05B5 from hkp server pgpkeys.mit.edu
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
$ gpg -a --export 437D05B5 | sudo apt-key add -


But debmirror still complains:

$ debmirror --nosource --host=archive.ubuntu.com --method=http --root=ubuntu --dist=hardy --section=main,restricted,universe,multiverse --arch=i386 --progress /media/disk/
Mirroring to /media/disk/ from [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
Arches: i386
Dists: hardy
Sections: main,restricted,universe,multiverse
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/hardy/Release... ok
[0%] Getting: dists/hardy/Release.gpg... ok
gpgv: Signature made Sat 20 Sep 2008 04:13:54 AM EEST using DSA key ID 437D05B5
[GNUPG:] ERRSIG 40976EAF437D05B5 17 2 00 1221873234 9
[GNUPG:] NO_PUBKEY 40976EAF437D05B5
gpgv: Can't check signature: public key not found
Release signature does not verify.
Errors:
 Release signature does not verify.
Failed to download some Release or Release.gpg files!
WARNING: releasing 1 pending lock...

---

### Post by benj.david on 2009-10-05
Hi,
I hope that you've already found the solution...
Anyway, I had to face the same issue so a share the solution :
$ gpg --export 437D05B5 >> ~/.gnupg/trustedkeys.gpg

You will be able to launch to debmirror command again.
ben

---

### Post by Lars Noodén on 2009-10-05
Thanks for the follow up.

---

