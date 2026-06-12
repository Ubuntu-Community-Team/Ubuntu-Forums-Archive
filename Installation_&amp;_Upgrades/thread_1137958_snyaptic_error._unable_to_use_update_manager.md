---
title: "snyaptic error. unable to use update manager"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by rraffii on 2009-04-26
I was doing updates on a fresh Ubuntu 8.10 install. the update manager installed all the software except the "visual effect extra" im a super noob to linux.i just figured out how to install flash 64bit!!! lol  Plez  help these are the errors im getting

#1    This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'

#2   An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '&#8220;deb' is not known on line 39 in source list /etc/apt/sources.list, E:The list of sources could not be read.

         [B][U][SIZE="4"]  Source list
[/SIZE][/U][/B]
# 
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main restricted

deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main&#8221;
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main&#8221;
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main&#8221;
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed universe main multiverse restricted
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main&#8221;

also i cannot edit this list i don't have permission.

---

### Post by lisati on 2009-04-26
From the terminal, try the following and let us know how you get on:
```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by rraffii on 2009-04-26
> **lisati said:**
> From the terminal, try the following and let us know how you get on:
```
sudo apt-get update
sudo apt-get install -f
```

this is wat i been getting for the last 2 hr when i tried to is that command..im getting OWN3D!!!

```
E: Type '“deb' is not known on line 39 in source list /etc/apt/sources.list
```

---

### Post by Partyboi2 on 2009-04-26
You  have incorrect entries in your sources.list as well as mixing different releases repos can cause breakages. I would suggest deleting from your sources.list
```
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main&#8221;
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main&#8221;
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main&#8221;
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main&#8221;
```Open a terminal and
```
gksu gedit /etc/apt/sources.list
``` delete or comment (#) out those repos and save then back in the terminal
```
sudo apt-get update
```

---

### Post by rraffii on 2009-04-26
> **Partyboi2 said:**
> You  have incorrect entries in your sources.list as well as mixing different releases repos can cause breakages. I would suggest deleting from your sources.list
```
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”
```Open a terminal and
```
gksu gedit /etc/apt/sources.list
``` delete or comment (#) out those repos and save then back in the terminal
```
sudo apt-get update
```


It work ..Thank You Very Much.

i been tryin to figure this out on my own scenes last night.

---

