---
title: "missing PUBKEY error"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by jimwhitend on 2009-09-20
I added and removed some third party software sources and now Update Manager return this error below. What to do? Thanks.
-JimW

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

---

### Post by tgeer43 on 2009-09-21
Copy and paste the following into the console.
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
gpg --armor --export 40976EAF437D05B5 | apt-key add -
```That should set things straight.
The first line gets the requested key from a keyserver.
The second line exports the key from gpg and adds it to your list of trusted keys.

tgeer

---

### Post by jimwhitend on 2009-09-22
Thanks tgeer, 
but all I get from the first command (after a half dozen attempts) is:

~$ gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server wwwkeys.eu.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
 
Is this likely to be a keyserver error, or my problem? Thanks again.
-JimW

---

### Post by wojox on 2009-09-22
Try:

```
gpg --keyserver keyserver.ubuntu.com --recv 40976EAF437D05B5

```

```
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
```

---

### Post by jimwhitend on 2009-09-22
Same error.

---

### Post by tgeer43 on 2009-09-22
I dunno guy. Both keyservers work here. Just tried 'em.

tgeer

---

