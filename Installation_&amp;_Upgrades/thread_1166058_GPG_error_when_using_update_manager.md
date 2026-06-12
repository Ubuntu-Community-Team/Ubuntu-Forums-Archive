---
title: "GPG error when using update manager"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by thanwinnaing on 2009-05-21
hello!
when I try to update using update manager, this error occur.

```
W: GPG error: http://archive.canonical.com jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: http://mm.archive.ubuntu.com jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://mm.archive.ubuntu.com jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

how to solve this problem? please

---

### Post by spcwingo on 2009-05-21
Try this:

[http://ubuntuforums.org/showthread.php?p=1653773]("http://ubuntuforums.org/showthread.php?p=1653773")

It worked for me.

---

### Post by thanwinnaing on 2009-05-21
Thanks 

I will try this.

---

### Post by thanwinnaing on 2009-05-26
> **spcwingo said:**
> Try this:

[http://ubuntuforums.org/showthread.php?p=1653773]("http://ubuntuforums.org/showthread.php?p=1653773")

It worked for me.

hello!
when I try this,it appear.
how to solve?

```
gpg --keyserver subkeys.pgp.net --recv 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

---

### Post by spcwingo on 2009-05-26
I think it's a problem with your sources.list.  Please post your sources.list (/etc/apt/sources.list).

---

### Post by thanwinnaing on 2009-05-27
thanks for all.

now I'm OK.

I change server from Update Manager setting.
When I click 'select best server', it choose new mirror server for me.
And not shown error in using update manager.

yours,
:p:p:p

---

