---
title: "Can't update or remove evolution"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by paincakes on 2009-03-07
Hi!

I have a big problem!
Evolution-common is reporting an error.

When i do for example: apt-get install curl i get:

```

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  evolution: Depends: evolution-common (= 2.24.3-0ubuntu1) but 2.24.2-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

And when i do apt-get -f install i get the following :

```

root@sandbox-server:/var/www# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  evolution-common
The following packages will be upgraded:
  evolution-common
1 upgraded, 0 newly installed, 0 to remove and 61 not upgraded.
3 not fully installed or removed.
Need to get 0B/16.8MB of archives.
After this operation, 81.9kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing /var/cache/apt/archives/evolution-common_2.24.3-0ubuntu1_all.deb (--unpack):
 files list file for package `libedataserver1.2-11' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/evolution-common_2.24.3-0ubuntu1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Partyboi2 on 2009-03-07
Open a terminal and try
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libedataserver1.2-11.list
```then
```
sudo apt-get -f install
```

---

### Post by paincakes on 2009-03-07
> **Partyboi2 said:**
> Open a terminal and try
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libedataserver1.2-11.list
```then
```
sudo apt-get -f install
```

You my friend, is a damn star! LOVE YOU!!
This fixed my problem! Thanx a bunch :))))

*gives Partyboi2 a cookie*

---

