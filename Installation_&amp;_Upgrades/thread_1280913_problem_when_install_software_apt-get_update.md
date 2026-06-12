---
title: "problem when install software apt-get update"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by eAi-T0ky0 on 2009-10-02
when i trying to download any thing from add\remove or symantic it give me error msg

```
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513
W: GPG error: http://ftp.oleane.net hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://ftp.oleane.net/ubuntu/dists/hardy-updates/main/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
```


:(

---

### Post by BorgHunter on 2009-10-02
Try
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 665F9AEFE1098513

```
to fix the first error, at least.

---

### Post by eAi-T0ky0 on 2009-10-02
thanks for replay bro , I do the command and do 'sudo apt-get update' and ya pretty right it fix the first error , but what about the second error and third? :( I can't download anything from synaptic or add\remove

---

### Post by markbuntu on 2009-10-02
The servers are a little busy today. Try again later.

---

