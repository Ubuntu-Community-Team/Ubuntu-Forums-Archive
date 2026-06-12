---
title: "Update error fixing"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by John Greenly Steel on 2009-06-05
How do I deal with an update that does not work? All I get is an error message as follows:-

E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version

It was worse with the first 294 updates after I installed Ubuntu. 5 error were found and there was no way of skipping these that a beginner like me could fathom out. Why is it not fully automated?

I hate to say it but my WINDOWS system does all this automatically with no effort on my part!:(

---

### Post by zvacet on 2009-06-06
Type in terminal

```
sudo apt-get -f install
```

```
sudo apt-get dpkg --configure -a
```

If you get any errors post it here.

---

