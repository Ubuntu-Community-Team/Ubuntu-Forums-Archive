---
title: "Strange apt-get gpg key error"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by brightJoker on 2009-02-13
Sometime last week, not exactly sure when, but my apt-get update started producing this message:
```

W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E931CE221789C97
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C71839136CF5CE97
W: You may want to run apt-get update to correct these problems
brightjoker@brightjoker-laptop:~$ 

```
I know I have to install keyring, but not sure which one.  Any help is appreciated as always :)

---

### Post by sisco311 on 2009-02-13
Download launchpad-update-final.zip from: [http://ubuntuforums.org/showpost.php?p=6638010&postcount=42]("http://ubuntuforums.org/showpost.php?p=6638010&postcount=42")

Extract it in your home directory and run it:
```
sudo ~/launchpad-update intrepid
```
then:
```
sudo apt-get update
```

---

### Post by brightJoker on 2009-02-13
Thank you working like a charm now :)

Edit:  Random other question though about my Third Party sources, in the gui Software Sources, do I need to have both the repos selected with and without "(source)" at the end or just one or the other?

---

### Post by forger on 2009-02-14
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by sisco311 on 2009-02-14
> **forger said:**
> [http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

Thanks for the link and script. :)

---

