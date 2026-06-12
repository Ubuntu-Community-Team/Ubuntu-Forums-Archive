---
title: "Upgrade from 7.04 to 7.10 ubuntu ps3"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by dgrzalja on 2009-04-02
Hi!
I have been trying to update via 'Update Manager' in Ubuntu.
I read Upgrade notes on Ubuntu site and changed sources.list to match
the ones site requested.. I updated the software...
Then i clicked on Upgrade button next to 'New distribution release 7.10 is
available'.
And Ubuntu starts the upgrade but an error appears:

```

Failed to fetch http://wine.budgetdedicated.com/apt/dists/feisty/Release Unable to   find expected entry  main/binary-powerpc/Packages in Meta-index file (malformed Release file?)
```


I have another question. I noticed that my partition has 2.5Gb of free space, partition size is 10Gb. How can I free up some space? I allready deleted everything i downloaded in Home directory.

Please help.. Thanks!

---

### Post by Partyboi2 on 2009-04-02
You need to disable 3rd party repos before upgrading. Open up software Sources (System>Admin>Software Sources) and on the 3rd party tab untick  the wine repo.

To free up some space you could use 
```
sudo apt-get autoclean
sudo apt-get clean


```
This will clean out local repository of retrieved packages. If you still want to go further have a look at [[COLOR=Blue]this[/COLOR]]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html")

---

### Post by dgrzalja on 2009-04-05
Thanks for your reply. 
Eventualy i just install 8.10 from scratch..

---

### Post by priyankav on 2009-04-05
how did you reinstall 8.1 instead of 7.04..?
did you install it on top of the existing ubuntu 7.04?
plz detail how you organized the partitions?

---

### Post by dgrzalja on 2009-04-05
I installed petiboot, downloaded Xubuntu iso and burned it
to a cd.
Then i booted that cd and started instalation.
I reformated entire hard drive.

But, i'm not satisfied with 8.10, Wifi and sound are not 
working for me. I tryed to install a new kernel (2.26.9) 
but after booting it, system hangs right when it should enter
X. Screen flashes and just hangs... My only option is then to
shut down manualy and boot the old kernel back.

I'm thinking about YDL, since i heard it's better on ps3 than ubuntu.

---

