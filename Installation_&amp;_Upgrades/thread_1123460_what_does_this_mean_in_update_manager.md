---
title: "what does this mean in update manager"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by DarinB on 2009-04-12
what does this mean 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7

---

### Post by drs305 on 2009-04-12
Launchpad has added security features. To add the key, run these:
```

gpg --keyserver keyserver.ubuntu.com --recv 4874D3686E80C6B7    
gpg --export --armor 4874D3686E80C6B7 | sudo apt-key add -
sudo apt-get update

```

---

### Post by DarinB on 2009-04-12
thanks not sure what i did but the error is gone

---

