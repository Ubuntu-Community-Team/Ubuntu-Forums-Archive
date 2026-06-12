---
title: "sudo upgrade signature canot be verified"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by MatthewAPeters on 2009-02-19
Update for sudo cannot verify signature.  This is one piece of software I don't want to update with unsigned code!

Ubuntu 8.04

Version 1.6.9p10-1ubuntu3.4:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5227BEBD68436DDF

Now what?

---

### Post by whoop on 2009-02-19
Give it some time. This problem usually solves itself. Allot of times it is just a server error, and it will work later on.

---

### Post by forger on 2009-02-20
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

### Post by zika on 2009-02-20
> **MatthewAPeters said:**
> Update for sudo cannot verify signature.  This is one piece of software I don't want to update with unsigned code!
Ubuntu 8.04
Version 1.6.9p10-1ubuntu3.4:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5227BEBD68436DDF
Now what?

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 5227BEBD68436DDF
gpg --export --armor 5227BEBD68436DDF | sudo apt-key add -
```

---

### Post by binbash on 2009-02-20
[http://ubuntuforums.org/showpost.php?p=6767198&postcount=3](http://ubuntuforums.org/showpost.php?p=6767198&postcount=3)

---

### Post by MatthewAPeters on 2009-02-24
> **binbash said:**
> [http://ubuntuforums.org/showpost.php?p=6767198&postcount=3](http://ubuntuforums.org/showpost.php?p=6767198&postcount=3)

Why wouldn't Canonical build this into their product?  I don't expect them to maintain keys for third party, but for their own (supported) stuff?  kinda weak, no?

---

### Post by MatthewAPeters on 2009-02-24
> **zika said:**
> ```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 5227BEBD68436DDF
gpg --export --armor 5227BEBD68436DDF | sudo apt-key add -
```

Thank you, Zika!

---

### Post by MatthewAPeters on 2009-02-24
> **whoop said:**
> Give it some time. This problem usually solves itself. Allot of times it is just a server error, and it will work later on.

that didn't work.  zika's post did, though.  Thanks for responding.

---

