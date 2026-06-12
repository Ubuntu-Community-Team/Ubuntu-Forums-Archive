---
title: "Complete newbie requires help (No Public Key)"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by john28150 on 2009-08-08
Please excuse my ignorance but I am a complete newbie to Ubuntu/Linux (Ubuntu 8.04LTS) having only moved from the dark side a couple of days ago.

I have tried to use Update Manager this morning and have received the following error message:-

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6

Could somebody please explain what I need to do to correct the situation.

Regards

John28150

---

### Post by Partyboi2 on 2009-08-08
Hi, you need to add the key, to do this open a terminal (Applications>Accessories>Terminal) and add the key with
```
gpg --keyserver keyserver.ubuntu.com --recv 632D16BB0C713DA6
gpg --export --armor 632D16BB0C713DA6  | sudo apt-key add -
```
then
```
sudo apt-get update
```

---

### Post by john28150 on 2009-08-08
Great

All sorted

Cheers

john28150

---

