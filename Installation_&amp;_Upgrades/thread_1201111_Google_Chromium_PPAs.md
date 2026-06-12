---
title: "Google Chromium PPAs"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by Nima1972 on 2009-06-30
Hi.  Any help on this would be appreciated.

I'm trying to add the Chromium PPAs to my software sources but when I click reload I get the following:

An Error Occurred:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5

What does this mean?  How can it be fixed?

Thanks.

---

### Post by gradinaruvasile on 2009-06-30
U should add the PPA s keys to your keyring

In a terminal type:

```
gpg --keyserver keyserver.ubuntu.com --recv 5A9BF3BB4E5E17B5
gpg --export --armor 5A9BF3BB4E5E17B5 | sudo apt-key add -
sudo apt-get update

```

---

### Post by Nima1972 on 2009-06-30
Thanks gradinaruvasile, it accepted the two PPA's.  I deleted the two entries from my software sources and added them again with no error message.

Though I'm thinking this isn't the way to go to have the most latest release of chromium.

---

