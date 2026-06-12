---
title: "[SOLVED] Ubuntu 8.10 Update Problems!"
date: 2008-11-01
forum: General Help
---

### Post by ManosMark on 2008-11-01
Hi all. I have a problem in my Ubuntu 8.10. I go to update manager and I check for updates. The manager downloads some files and then i take this error message:
[[IMG]http://img507.imageshack.us/img507/8500/ddim1.th.jpg[/IMG]](http://img507.imageshack.us/my.php?image=ddim1.jpg)[[IMG]http://img507.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Can you help me? Thanx in advance

---

### Post by mahirh on 2008-11-01
try changing the download mirror

---

### Post by CatKiller on 2008-11-01
That message says that you haven't got the GPG key to authenticate the Medibuntu servers. Follow the instructions [here]("https://help.ubuntu.com/community/Medibuntu").

---

### Post by ManosMark on 2008-11-09
Thanks a lot mate. Porblem solved.

---

### Post by alinaqvi on 2009-04-18
[I] have a similare problem. here is the message

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  

W: Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/intrepid/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/I]

---

