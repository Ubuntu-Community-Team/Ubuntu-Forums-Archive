---
title: "Reload synaptic"
date: 2008-10-25
forum: General Help
---

### Post by hndaklr8480 on 2008-10-25
hey everyone i am having a wonderful time with linux it is the best think i have ever done.  there is nothing like doing and learning at the same time need some help with a problem:

W: GPG error: [http://deb.mulx.net](http://deb.mulx.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B1F5957DE4946268

I get this error everytime i reload synaptic any ideas

---

### Post by geirha on 2008-10-25
Sounds like you've added a repository without the corresponding key. 

Run the apt-key command explained here.
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

```
wget -q http://deb.mulx.net/pol.gpg -O- | sudo apt-key add -
```

---

### Post by hndaklr8480 on 2008-10-25
thanx u for that lightning response.  It work well thanx again

---

