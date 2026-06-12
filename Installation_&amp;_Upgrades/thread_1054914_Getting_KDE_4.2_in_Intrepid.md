---
title: "Getting KDE 4.2 in Intrepid"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by anjanesh on 2009-01-30
Im on a Kubuntu 8.10 64-bit and I want to update to KDE 4.2
I added deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main
When I did a sudo apt-get update, at the end I got this :
```
Fetched 500B in 2s (177B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
anjanesh@be3:~$
```

---

### Post by Branimir on 2009-01-30
Perhaps sites are down? Recently medibuntu and wine 
repositories are very often down.

Greetsa, Branimir.

---

### Post by blackgr on 2009-01-30
[http://ubuntuforums.org/showthread.php?t=1047743&page=5](http://ubuntuforums.org/showthread.php?t=1047743&page=5)

check this please

---

### Post by abn91c on 2009-01-30
> **anjanesh said:**
> Im on a Kubuntu 8.10 64-bit and I want to update to KDE 4.2
I added deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main
When I did a sudo apt-get update, at the end I got this :
```
Fetched 500B in 2s (177B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
anjanesh@be3:~$
```
did you follow the [http://www.kubuntu.org](http://www.kubuntu.org) instructions, the command for the PUBKey is there also

---

### Post by sprince09 on 2009-01-30
Awesome, solved my problem using regular Ubuntu 8.10 also. Thanks a lot!

---

### Post by anjanesh on 2009-01-30
> **abn91c said:**
> did you follow the [http://www.kubuntu.org](http://www.kubuntu.org) instructions, the command for the PUBKey is there also
I did a 
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
```
But something was happening - no clue what it was

---

### Post by anjanesh on 2009-01-30
```
anjanesh@be3:~/www$ gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
gpg: requesting key 493B3065 from hkp server keyserver.ubuntu.com
gpg: key 493B3065: "Launchpad PPA for Kubuntu Most Experimental Packages" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
OK
anjanesh@be3:~/www$
```

---

### Post by enaction on 2009-02-02
anjanesh, thanks for the fix key code.  i substituted in my no_pubkey # and that fixed the problem. -enaction

---

