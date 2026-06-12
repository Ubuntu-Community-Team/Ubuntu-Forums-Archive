---
title: "Incomplete upgrade to 8.10"
date: 2008-10-31
forum: General Help
---

### Post by pikabuntu on 2008-10-31
I started an upgrade to intrepid, but my computer locked up and it was incomplete.  Now, I need to know how to complete the upgrade.  How could I fix this?

---

### Post by ztrange on 2008-10-31
Whats your status? Is X working?, What was the error that stopped the upgrade?, What steps did you follow to upgrade and where did it failed? You need to provide some more info anytime you ask a question.

---

### Post by BackwardsDown on 2008-10-31
Just run the update manager again?

---

### Post by pikabuntu on 2008-10-31
Sorry :)

I was upgrading thru the update manager. It downloaded the upgrade tool, but it didn't download any packages.  Then it locked up when it was trying to install the packages that weren't there.

x is fine, everything is running normal.
except (screenshots included):

the system monitor thinks im in intrepid and
the update manager says I have 793 updates (presumably the packages that didn't download during the upgrade)

THen the update manager says it cant upgrade me from hardy to intrepid.

---

### Post by pikabuntu on 2008-10-31
Would upgrading from the alt. installation disk for intrepid be better?

---

### Post by ztrange on 2008-11-01
it seems that the upgrade manager is trying to upgrade to harde from intrepid...

I upgraded my hardy following this guide but it is in spanish

[http://www.ubuntu-es.org/index.php?q=node/100940](http://www.ubuntu-es.org/index.php?q=node/100940)

Anyway, it says 

Backup sources file
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.res
```

Edit the sources file and erase everything but the first line. Leave that first line commented with #
```
sudo gedit /etc/apt/sources.list
```

Launch update manager and it will show the upgrade to hardy button.
```
sudo update-manager -d
```

Well that is what I did. But it gave me an error at the middle of the procedure. I simply executed the sudo update-manager -d again and clicked the partial upgrade. Now everything is fine.

Now, Im wondering if maybe the problem that you have is because your sources file is not empty, so you may want to empty it and use the sudo update-manager -d command after it. 

Hope it helps

---

### Post by pikabuntu on 2008-11-01
that did not work for me....
It just thought that there were no updates available

---

