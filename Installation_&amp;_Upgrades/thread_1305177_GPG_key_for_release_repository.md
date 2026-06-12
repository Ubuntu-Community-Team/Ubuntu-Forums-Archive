---
title: "GPG key for release repository?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by gf_gollum on 2009-10-29
I'm getting this error when I try to update - I assume that I need a GPG key for the release repository - bbut I'm unable to find it mentioned anywhere. Please can you advise on how to fix this error:-
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C18DC20E89617F48

Thanks
Graham

---

### Post by Stemp on 2009-10-29
The key server are overloaded.
It's not very important for now, tomorrow you'll have to type this command : 
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C18DC20E89617F48
```

---

### Post by gf_gollum on 2009-10-29
Aaahh!.. so the answer was staring me in the face. Looks like the other text is all standard pre-amble - with the key ref. stuck on the end. Fine. I'll remember that for the future. Also  - yes it does look like the key server is overloaded :-)
Thx
G.

---

