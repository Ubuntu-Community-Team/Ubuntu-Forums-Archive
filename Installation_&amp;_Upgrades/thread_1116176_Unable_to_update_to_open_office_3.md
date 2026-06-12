---
title: "Unable to update to open office 3"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by Rishinature on 2009-04-04
I am trying to install open office 3 in hardy. I am not able to add the key to the software sources; its just not functioning. However if I right click on the key file and say "open with import key", I get a message that the key has been added. But I cannot see it in the list.

Now when I try to update, I get the following errors.
I had installed Ubuntu Tweak a few days ago. Do you think that might be causing the probelm.

Help!


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

---

### Post by Partyboi2 on 2009-04-04
Open a terminal (Applications>Accessories>Terminal) and try adding the 2 keys 
```
gpg --keyserver keyserver.ubuntu.com --recv 665F9AEFE1098513
gpg --export --armor 665F9AEFE1098513 | sudo apt-key add -
```for the second
```
gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
```
then
```
sudo apt-get update
```

---

### Post by Rishinature on 2009-04-05
Thank you very much. Could get the office 3 up and running finally:)

---

