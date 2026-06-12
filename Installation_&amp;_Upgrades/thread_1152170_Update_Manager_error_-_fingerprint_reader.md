---
title: "Update Manager error - fingerprint reader"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by ellison2011 on 2009-05-07
Hi

I recently attempted to install the fingerprint reader from lauchpad.
However, when I do a system update using update manager, I receive:
"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 084AF32EC2A6B0B1"
Clicking OK, clears the message, and update manager continues.

I don't need to use the scanner, as this is only a test system, but can anyone offer some advice on how to remove the software and stop the error.
The app does not appear in add/remove applications.

I'm using a Dell Latitude D430 running Ubuntu 9.04

Cheers

---

### Post by Partyboi2 on 2009-05-08
Hi, all you need to do is add the key to use that repo, open a terminal (Applications>Accessories>Terminal) and
type or paste

```
gpg --keyserver keyserver.ubuntu.com --recv 084AF32EC2A6B0B1
gpg --export --armor 084AF32EC2A6B0B1  | sudo apt-key add -
```

If you don't want the repo then open up Software Sources (System>Admin>Software Sources) and under the 3rd party repo tab remove the ppa.

---

### Post by ellison2011 on 2009-05-08
Thanks Partyboi2
I've removed launchpad.net from the list of Third Party Software sources and it's stopped the messages from appearing, so that's good enough for me.

Thanks for getting back to me so quick.:KS

---

