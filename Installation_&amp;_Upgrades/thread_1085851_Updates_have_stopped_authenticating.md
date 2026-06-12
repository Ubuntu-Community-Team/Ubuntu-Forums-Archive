---
title: "Updates have stopped authenticating"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by kentcb on 2009-03-03
I am running Intrepid. Sometime last week I started getting errors when attempting to apply updates. If I force the Update Manager to check for updates, I get this:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680
```


If I click the Install button I am told that XMBC-related packages cannot be authenticated.

Do I need to worry about this? Should I just install anyway?

Thanks,
Kent

---

### Post by Partyboi2 on 2009-03-03
You should be ok to install. You can add the new key by opening a terminal and
```
gpg --keyserver keyserver.ubuntu.com --recv 43C0AFF0D7FAE680
``````
gpg --export --armor 43C0AFF0D7FAE680 | sudo apt-key add -
```then
```
sudo apt-get update
```

---

### Post by forger on 2009-03-04
Here's a script, it can fix ppa links and get gpg keys:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by kentcb on 2009-03-04
That did it. Thank you very much!

---

### Post by p4tr1ck on 2009-03-04
:popcorn::P
Thank you so much !
:P

---

### Post by soheil on 2009-03-06
thank you Partyboi2  :popcorn:

---

