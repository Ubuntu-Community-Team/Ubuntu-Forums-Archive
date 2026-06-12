---
title: "Problem with update"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by zgembo on 2009-04-18
Hi, when I try sudo apt-get update I get this message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

:(

What's wrong here, somebody can help?

---

### Post by Ericyzfr1 on 2009-04-18
> **zgembo said:**
> Hi, when I try sudo apt-get update I get this message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

:(

What's wrong here, somebody can help?

If you go on the medibuntu webiste, you should be able to import the KEY that is a signature for the packages. Copy / paste to a text file, them in your software source....import key ( text file) and update your packages.

---

### Post by zgembo on 2009-04-18
Thanks, I'll try.

---

### Post by drs305 on 2009-04-18
This is the new all-encompassing medibuntu command for adding repositories and keyrings. Unlike past commands, it is no longer unique for a specific ubuntu version (jaunty, intrepid, etc):
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

```

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

