---
title: "Upgrade to 9.04 from to 8.10 stalls immediately"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by lostinUHF on 2009-05-02
I click on upgrade and a progress bar comes up and down load the first two files and then the process stops.  Nothing more happens in the upgrade.

I am up to date on my updates for 8.10 so what is happening here?

---

### Post by zvacet on 2009-05-02
I don´t know what reason is but you can always run 

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by lostinUHF on 2009-05-03
That does not work either.  My system thinks it is up to date with the latest dist but it is not.

See my output below:


Fetched 2443B in 1s (1756B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
thor@mark-desktop:~$

---

### Post by lostinUHF on 2009-05-03
e: Upgrade to 9.04 from to 8.10 stalls immediately
That does not work either. My system thinks it is up to date with the latest dist but it is not.

See my output below:


Fetched 2443B in 1s (1756B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
thor@mark-desktop:~$
lostinUHF is online now Report Post   	Edit/Delete Message

---

