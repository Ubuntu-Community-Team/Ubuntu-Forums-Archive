---
title: "iTunes Streaming with mt-daapd"
date: 2005-12-06
forum: General Help
---

### Post by damonkohler on 2005-12-06
So I installed mt-daapd and got my iTunes streaming working. The only problem is that to do it, I had to use dpkg --force-depends. Now I can't use apt-get because it's always complaining:

```

>:~/$ sudo apt-get install id3tool
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mt-daapd: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

>:~/$ sudo apt-get -s -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  mt-daapd
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
Remv mt-daapd [0.2.3-1]

```

Any suggestions?

---

