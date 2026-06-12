---
title: "were do i get this public key?"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by vistadude on 2009-02-13
i get an error saying 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

so, were can i get this public key?

---

### Post by cariboo on 2009-02-13
Each ppa has it's own public key. See the screenshot I have circled the part that that has a link called **follow these instructions**

Jim

---

### Post by Mud.Knee.Havoc on 2009-02-13
Instructions are here: [http://my-it-dump.blogspot.com/2009/02/fixing-gpg-errors-nopubkey-in-apt-get.html](http://my-it-dump.blogspot.com/2009/02/fixing-gpg-errors-nopubkey-in-apt-get.html)

---

### Post by linux_tech on 2009-02-13
If there is a missing GPG key, then in the terminal type-

Code:
```

gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF



gpg --export --armor 60D11217247D1CFF | sudo apt-key add -

```
This should add the key to the list.

---

### Post by forger on 2009-02-14
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

