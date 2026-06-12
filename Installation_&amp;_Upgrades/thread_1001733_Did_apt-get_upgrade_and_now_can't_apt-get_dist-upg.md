---
title: "Did apt-get upgrade and now can't apt-get dist-upgrade"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by trubblemaker on 2008-12-04
I'm on 2.6.17-13-386.  I ment to do a dist-upgrade to 'intrepid'.  So I updated my source files and then ran
```
sudo apt-get update && sudo apt-get update && sudo apt-get upgrade
```

Now I can't do

```
sudo apt-get upgrade
```

I get an error:
```
E: Internal Error, Could not perform immediate configuration (1) on libc6

```
I tried to install libc6 and I get:
```
The following packages have unmet dependencies:
  libc6: Depends: findutils (>= 4.4.0-2ubuntu2) but 4.2.27-3 is to be installed
  libc6-dev: Depends: libc6 (= 2.4-1ubuntu12.3) but 2.8~20080505-0ubuntu7 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.4-1ubuntu12.3) but 2.8~20080505-0ubuntu7 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Needless to say apt-get -f install doesn't work.  Anyone got any ideas?

I tried aptitude but it wasn't helpful either.

---

### Post by meindian523 on 2008-12-04
Don't do a sudo apt-get dist-upgrade.Instead,upgrade to Intrepid through the update manager.dist-upgrade won't work because Ubuntu upgrades need a few files pulled in from different places to correctly upgrade.See
[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

EDIT:
Please check your first code box.I think you meant ```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by snowpine on 2008-12-04
Hi Trubblemaker,

2.6.17 is 6.10 Edgy, if I'm not mistaken? Frankly I think your best bet is to back everything up and reinstall. There is no good upgrade path from Edgy to Intrepid that I'm aware of. :(

---

### Post by jenkinbr on 2008-12-04
Actually, I think it's gutsy.

or not!  I checked [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and searched for 'kernel' in each section that was availible.  It must be Edgy, which no longer exsists in the repositories because it has reached End Of Life.

As suggested by snowpine, you will need to do a fresh reinstall, so be sure to back up everything, then download an intrepid Ibex cd ( [http://www.ubuntu.com/getubuntu/download/](http://www.ubuntu.com/getubuntu/download/) ), burn it, and install it.

---

### Post by trubblemaker on 2008-12-04
Thanks for the help, I was hoping for another answer...

I *think* my home directory is on a separate partition (and is safe) so I guess I'll just nuke it(my install).

Just in case anyone else stumbles on this I wasn't able to install update-manager-core as it generated the same error as above.  Truly I'm in a bad state...

---

