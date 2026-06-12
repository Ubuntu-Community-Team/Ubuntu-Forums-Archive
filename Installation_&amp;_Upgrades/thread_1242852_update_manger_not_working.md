---
title: "update manger not working"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by BigBig5 on 2009-08-17
I get an error when I cheak for ne updates.
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Don't know where to get the key? Thanks for all the help!

---

### Post by oldos2er on 2009-08-17
Run ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```and type in "yes" when prompted.

---

### Post by Catiline on 2009-08-18
> **oldos2er said:**
> Run ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```and type in "yes" when prompted.

I am getting the same issue when I run the above in Terminal.  I'm given the output:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

What next please?

---

### Post by Katalog on 2009-08-18
Try running this command instead:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

---

### Post by Catiline on 2009-08-18
Excellent, thank you!

That seems to have fixed it :-)

---

