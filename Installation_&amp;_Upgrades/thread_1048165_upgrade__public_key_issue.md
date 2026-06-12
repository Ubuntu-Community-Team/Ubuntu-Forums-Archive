---
title: "upgrade / public key issue"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by bionnaki on 2009-01-23
[I]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2BA7BC59D745C5EB
W: You may want to run apt-get update to correct these problems[/I]

how do I solve this?

---

### Post by Partyboi2 on 2009-01-23
Try this,

```
gpg --keyserver keyserver.ubuntu.com --recv 2BA7BC59D745C5EB
``````
gpg --export --armor 2BA7BC59D745C5EB | sudo apt-key add -
```then
```
sudo apt-get update
```

---

### Post by bionnaki on 2009-01-23
this is what I get:

 
gpg --keyserver keyserver.ubuntu.com --recv 2BA7BC59D745C5EB
gpg: requesting key D745C5EB from hkp server keyserver.ubuntu.com
gpg: can't open `/home/bionnaki/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

sudo gpg --keyserver keyserver.ubuntu.com --recv 2BA7BC59D745C5EB
gpg: WARNING: unsafe ownership on configuration file `/home/bionnaki/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

---

### Post by bionnaki on 2009-01-23
any ideas?

---

### Post by Partyboi2 on 2009-01-24
Lets check the file permission
```
ls -l home/bionnaki/.gnupg/pubring.gpg
```

---

### Post by blackgr on 2009-01-24
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743) check this out

---

### Post by bionnaki on 2009-01-24
> **blackgr said:**
> [http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743) check this out

worked.
thanks

---

