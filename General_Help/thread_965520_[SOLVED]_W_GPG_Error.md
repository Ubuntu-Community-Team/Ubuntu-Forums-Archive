---
title: "[SOLVED] W: GPG Error"
date: 2008-10-31
forum: General Help
---

### Post by Toribor on 2008-10-31
When I google the error code I find a lot of posts of people having the same problem, but I haven't been able to find a fix yet. I'm still running Hardy for right now, trying to upgrade to Ibex (Yay for no more xorg.conf)

When I run the update manager, or try to run *Sudo apt-get update* I get the following error message:


*W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783*

I've also read that this may be a temporary problem due to server strain or archive updates, is this the case or can I fix my problem now?

(I'm having issues with my dual monitor setup and I've heard intrepid is better at these types of problems so I'm anxious to fix the problem) Thanks in advance for any help!

---

### Post by drs305 on 2008-10-31
It may be server strain, but here are the commands to ensure you have the correct Medibuntu repository settings. Note they are version specific:

Intrepid 
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
Hardy
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by Toribor on 2008-10-31
Awesome! That allowed for a successful update, time for me to upgrade to Intrepid. Thank you!

---

