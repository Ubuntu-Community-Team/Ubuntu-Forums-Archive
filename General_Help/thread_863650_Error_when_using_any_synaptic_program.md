---
title: "Error when using any synaptic program"
date: 2008-07-18
forum: General Help
---

### Post by Tribulation on 2008-07-18
When I use Update Manager, or change repository servers or the like, I keep getting an error message

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I just click close and I can go on with up I'm doing, it doesn't hinder my changing of servers or checking for updates it's just annoying and I don't know why it started up all of a sudden.

---

### Post by plucky on 2008-07-18
> **Tribulation said:**
> When I use Update Manager, or change repository servers or the like, I keep getting an error message



I just click close and I can go on with up I'm doing, it doesn't hinder my changing of servers or checking for updates it's just annoying and I don't know why it started up all of a sudden.

You need to add the Medibuntu GPG key using this command```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` in a terminal window.


Good Luck

---

### Post by pdwerryhouse on 2008-07-18
apt/synaptic needs the medibuntu gpg added. Try this:

```
wget -O - http://packages.medibuntu.org/medibuntu-key.gpg | sudo apt-key add - 
```

---

### Post by Tribulation on 2008-07-19
Thanks, I used

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` 

and it cleared it right up.

---

