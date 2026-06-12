---
title: "Install from /var/cache/apt/archives without Internet?"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by Rami_961 on 2009-08-19
hi, i downloaded vlc and all of it's dependencies and i put them in /var/cache/apt/archives
and i want to install them without internet connection..how am i suppose to read vlc in Synaptic Package Manager to install it or if thre's any other way ?
//I'm new to linux

---

### Post by zvacet on 2009-08-19
Type in terminal 

```
sudo apt-get install vlc
```

---

### Post by Rami_961 on 2009-08-19
> **zvacet said:**
> Type in terminal 

```
sudo apt-get install vlc
```
I already done that but didn't work, i read in AptOnCd website that after copying packages to /var/cache/apt/archives i can install them with Synaptic offline, but isn't there's a way to open packagfes with synaptic?

---

### Post by oldos2er on 2009-08-19
Synaptic only looks to the repositories for packages. Instead, run
```
sudo dpkg -i /var/cache/apt/archives/*deb
```

---

### Post by Rami_961 on 2009-08-19
> **oldos2er said:**
> Synaptic only looks to the repositories for packages. Instead, run
```
sudo dpkg -i /var/cache/apt/archives/*deb
```
Thanks!

---

