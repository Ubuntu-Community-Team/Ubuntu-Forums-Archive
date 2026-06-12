---
title: "Getting an error when trying to update?????"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by mysticaltopher on 2009-03-18
When I run my update manager and click "check" for new updates it starts to download (48) new updates and at the end it gives me this error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

and then no new updates appear?

Anyone ever seen this before?  Any help would be great!
Thanks!

---

### Post by Partyboi2 on 2009-03-18
Looks like you need to add the key. Open a terminal (Applications>Accessories>Terminal) and 
```
 sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by mysticaltopher on 2009-03-18
That worked....Thanks!!!!

---

