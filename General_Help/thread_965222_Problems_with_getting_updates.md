---
title: "Problems with getting updates"
date: 2008-10-31
forum: General Help
---

### Post by vedran.omeragic on 2008-10-31
Problem occured just after fresh new installation of 8.10 
Whenever I try to update anything, or install anything or even install a simplest coded, I'm getting the following message:

```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

---

### Post by plucky on 2008-10-31
> **vedran.omeragic said:**
> Problem occured just after fresh new installation of 8.10 
Whenever I try to update anything, or install anything or even install a simplest coded, I'm getting the following message:

```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

That usually means that you have two package managers running on your system.Make sure you only have one package manager process running.

Good Luck

---

