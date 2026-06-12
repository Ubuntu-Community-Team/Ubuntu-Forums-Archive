---
title: "public key problem"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by lesterness on 2009-02-25
I just got the following error message while installing updates: "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF".

How do I install this public key?

Thanks.

Lesterness

---

### Post by sgosnell on 2009-02-25
You don't have to install it.  The message is just a warning, not an error.  It's warning you that apt has no key and can't verify the repository.  If you really want to install the key, read [this thread](http://ubuntuforums.org/showthread.php?t=387165) and the one referenced in it.  Searching here and in Google can give you lots of information.

---

### Post by forger on 2009-02-27
Update your Launchpad PPA links and keys:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by binbash on 2009-02-27
[http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

---

