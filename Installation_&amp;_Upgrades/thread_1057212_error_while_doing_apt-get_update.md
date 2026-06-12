---
title: "error while doing apt-get update"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by abovenewbi on 2009-02-01
hi, when I try to run the apt-get update command on the terminal I get the following error message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

any ideas?

---

### Post by taurus on 2009-02-01
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)

---

### Post by sisco311 on 2009-02-01
```
gpg --keyserver keyserver.ubuntu.com --recv 247d1cff
```
```
gpg --export --armor 247d1cff | sudo apt-key add -
```
and
```
sudo apt-get update
```
should also work.

---

### Post by abovenewbi on 2009-02-01
thanks for the response, there was an error when trying to run :
gpg --keyserver keyserver.ubuntu.com --recv 247d1cff

error:
gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: can't open `/home/victor/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

any Ideas?

---

### Post by sisco311 on 2009-02-01
> **abovenewbi said:**
> thanks for the response, there was an error when trying to run :
gpg --keyserver keyserver.ubuntu.com --recv 247d1cff

error:
gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: can't open `/home/victor/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

any Ideas?

Did you try the script in the link posted by taurus?
(post #42)

---

### Post by abovenewbi on 2009-02-01
ok...I've downloaded the zip file, how do i run it? what is the command for the terminal?

---

### Post by taurus on 2009-02-01
Assuming you saved it, launchpad-update.zip, to your desktop.  Open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
unzip -x launchpad-update.zip
sudo ./launchpad-update
```

---

### Post by sisco311 on 2009-02-01
Extract the file in your home directory(right click, extract to ...) and run it as root:
```
sudo ~/launchpad-update intrepid
```

---

### Post by abovenewbi on 2009-02-01
hi, Thanks for all your help... :) it works fine
Thanks to who wrote the script and for you guys who responded to the this thread

---

