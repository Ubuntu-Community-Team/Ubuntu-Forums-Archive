---
title: "Error when using update manager"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by timstone on 2009-04-27
I get this when I try to run update manager but it doesn't give me the message if I run with root.

```
W: GPG error: http://ppa.launchpad.net hardy Release: 
The following signatures couldn't be verified because the public key is not available: 
NO_PUBKEY 6AF0E1940624A220

```

any idea what the problem is?

---

### Post by Partyboi2 on 2009-04-28
Hi, you can add the key from the terminal
```
gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220
gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -
```

```
sudo apt-get update
```

---

### Post by paul1080 on 2009-10-26
Thanks, I had the same problem and this fixed it great.

---

