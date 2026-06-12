---
title: "Undo completely removed openssh in Synaptic"
date: 2008-08-27
forum: General Help
---

### Post by Stoneface on 2008-08-27
I completely removed openssh in Synaptic and would like to reinstall it again. How would I add openssh to Synaptic again or do I need to install it in a different way now? Please help me. I uninstalled because I thought it was easy to get the standard openssh configuration so I could connect to the server again, but now Synaptic package manager cannot find the package anymore....

---

### Post by iaculallad on 2008-08-27
Open your terminal:

```
sudo apt-get install openssh-server
```

---

### Post by Stoneface on 2008-08-27
Did that. Worked like a charm. Thanks iaculallad!

---

### Post by sameerds on 2008-08-27
> **Stoneface said:**
> I uninstalled because I thought it was easy to get the standard openssh configuration so I could connect to the server again

I think what you mean is that you wanted to remove all the keys and stuff that ssh had gathered in your account. The correct way to do that is to delete a hidden directory called ".ssh" in your home directory. Uninstalling the package won't touch that directory, since the pacakge considers that directory to be "your data", and would never touch it.


> **Stoneface said:**
> I completely removed openssh in Synaptic and would like to reinstall it again. <snip> now Synaptic package manager cannot find the package anymore....

> **iaculallad said:**
> Open your terminal:

```
sudo apt-get install openssh-server
```

> **Stoneface said:**
> Did that. Worked like a charm. Thanks iaculallad!

I didn't understand this part. Are you saying that when you used the search feature in Synaptic to search for "openssh" you found nothing, but the apt-get command worked? That's very very strange.

---

