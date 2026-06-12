---
title: "[SOLVED] what does this mean"
date: 2008-07-27
forum: General Help
---

### Post by DarinB on 2008-07-27
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Waappu on 2008-07-27
Hi

I do not know exactly. It related to key verification about repository. But you get rid of it by typing in terminal ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by DarinB on 2008-07-27
is this one long command, where are the breaks

---

### Post by Waappu on 2008-07-27
Hi

It is one command

You can see it also from community document
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by DarinB on 2008-07-28
i have no idea what any of this did but it seems to work
thanks

---

