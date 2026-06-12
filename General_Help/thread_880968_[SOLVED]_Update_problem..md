---
title: "[SOLVED] Update problem."
date: 2008-08-05
forum: General Help
---

### Post by LeadHop on 2008-08-05
Hello all - Just some issues i'm having with the updates...  Just recently, it started to show this message:

GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release.gpg](http://packages.medibuntu.org/dists/hardy/Release.gpg)  
Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2)  
Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.

It's strange since I've completely removed wine a few weeks ago and i've 'uncommented' the medibuntu stuff.  hope someone can help!  TIA!

---

### Post by Qchan on 2008-08-05
> **LeadHop said:**
> Hello all - Just some issues i'm having with the updates...  Just recently, it started to show this message:

GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263Failed to fetch [http://packages.medibuntu.org/dists/hardy/Release.gpg](http://packages.medibuntu.org/dists/hardy/Release.gpg)  
Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/free/i18n/Translation-en_US.bz2)  
Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/hardy/non-free/i18n/Translation-en_US.bz2)  
Some index files failed to download, they have been ignored, or old ones used instead.

It's strange since I've completely removed wine a few weeks ago and i've 'uncommented' the medibuntu stuff.  hope someone can help!  TIA!

[b][color=darkred]
Click on Applications --> Accessories --> Terminal.

Inside terminal, type 

> 
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list


Hope that fixes your issue
[/b][/color]

---

### Post by cdtech on 2008-08-05
You may also want to do a "sudo apt-get autoremove && sudo apt-get clean" as well to clean out your repository....

---

### Post by tech9 on 2008-08-05
> **cdtech said:**
> You may also want to do a "sudo apt-get autoremove && sudo apt-get clean" as well to clean out your repository....

also, you can change your mirror and reload in synaptic

---

### Post by LeadHop on 2008-08-05
thanks all; it took care of some of the problems but I'm still getting this malarkey:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by plucky on 2008-08-05
> **LeadHop said:**
> thanks all; it took care of some of the problems but I'm still getting this malarkey:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Try this line in a terminal

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

and then ```
sudo apt-get update
```

Good Luck

---

### Post by LeadHop on 2008-08-06
Thanks!  that took care of most of the problem, but i've noticed that now the update is incredibly slow.  Maybe it'll clear up later by itself, but i think i'm good for now!  Thank you!

---

