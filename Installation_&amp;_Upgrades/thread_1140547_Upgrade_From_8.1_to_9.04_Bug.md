---
title: "Upgrade From 8.1 to 9.04 Bug?"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by 9a8sy on 2009-04-27
I upgraded from version 8.1 to 9.04 the other day. During the process, it found a couple of items that would not install. A box came up that said I should report this as a bug and had a button to automatically do the report. I clicked the button but then it said it was unable to connect to send the report. Today I checked to see if I needed to do any updates. Two items come up but  they will will not allow me to check them to update. Those items are brasero CD/DVD burning application, and liblucene2-java search engine library. I assume these are related to the upgrade errors I had. How do I go about installing these upgrades?

---

### Post by cariboo on 2009-04-27
Open an Applcations-->Accessories-->Terminal and type:

```
sudo apt-get -f install
```

this will install any missing dependencies and partially installed packages. THen in the same terminal type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by 9a8sy on 2009-04-27
I tried your suggestion. After typing in the first command it suggested I remove some items by typing in another command which I proceeded to do. It asked if I was root so I went into system tools and root terminal. Root tried to open but could not. See below for what I did. How do I get root to open?

dennis@dennis-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcj-4.3-base libstrigiqtdbusclient0 libcommons-collections3-java libarts1c2a
  libartsc0 libxpp3-java amarok-engine-xine libgcj9-0 ttf-wqy-zenhei libgcj-bc
  libbackport-util-concurrent-java libxom-java libwxgtk2.6-0
  liblog4j1.2-java-gcj libjaxme-java ttf-kannada-fonts libregexp-java
  libjaxp1.3-java-gcj liblog4j1.2-java libjdom1-java liblucene2-java
  librasqal0 libxerces2-java-gcj ruby1.8 ruby libcommons-logging-java
  libcommons-codec-java libgcj-common ttf-telugu-fonts libjaxp1.3-java
  libwxbase2.6-0 libxpp2-java mbr libjline-java libgcj9-jar libxerces2-java
  libmjpegtools0c2a libsaxonb-java libtunepimp5 libifp4
  libcommons-beanutils-java libdvdread3 libdb-je-java libcommons-digester-java
  libdb4.5-java-gcj libdb4.5-java ttf-oriya-fonts libjtidy-java
  libservlet2.3-java libruby1.8 libdom4j-java ttf-bengali-fonts libnjb5
  libjaxen-java xutils-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

dennis@dennis-laptop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
dennis@dennis-laptop:~$

---

### Post by Elwro on 2009-04-28
I have a similar problem as the OP - namely, brasero doesn't allow me to check its name when choosing which updates to install. As suggested, I tried
```
sudo apt-get -f install
```but only got the result "0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.". I then tried
```
sudo apt-get update && sudo apt-get dist-upgrade
``` (as suggested) and after a standard wall of text this message was displayed:```
The following packages have been kept back:
  brasero
```The behaviour of the update manager hasn't changed.

What should I do now to update brasero? Just remove and reinstall?

---

### Post by jflaker on 2009-04-29
> **Elwro said:**
> I have a similar problem as the OP - namely, brasero doesn't allow me to check its name when choosing which updates to install. As suggested, I tried
```
sudo apt-get -f install
```but only got the result "0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.". I then tried
```
sudo apt-get update && sudo apt-get dist-upgrade
``` (as suggested) and after a standard wall of text this message was displayed:```
The following packages have been kept back:
  brasero
```The behaviour of the update manager hasn't changed.

What should I do now to update brasero? Just remove and reinstall?

I just dealt with that and resolved it by

```

sudo apt-get remove brasero && sudo apt-get install brasero

```

---

### Post by alphacrucis2 on 2009-04-29
> **Frugalfart said:**
> 

dennis@dennis-laptop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
dennis@dennis-laptop:~$

You can only have one copy of synaptic, apt etc running at a time.

---

### Post by Elwro on 2009-04-29
> **jflaker said:**
> I just dealt with that and resolved it by

```

sudo apt-get remove brasero && sudo apt-get install brasero

```Thanks!

---

### Post by Hydraah on 2009-05-19
> **alphacrucis2 said:**
> You can only have one copy of synaptic, apt etc running at a time.

Actually, it looks like he wasn't using sudo, just issued the command as a non-privileged user.

---

