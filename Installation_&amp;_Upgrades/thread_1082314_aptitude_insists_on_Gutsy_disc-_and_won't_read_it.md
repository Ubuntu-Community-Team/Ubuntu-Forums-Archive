---
title: "aptitude insists on Gutsy disc- and won't read it"
date: 2009-02-27
forum: Installation &amp; Upgrades
---

### Post by David J Bush on 2009-02-27
My last dvd install was 7.10, Gutsy. Since then I have upgraded online. I am currently using Kubuntu 8.10. I prefer to use aptitude for day to day upgrades because it does the best job of recognizing and resolving conflicts and dependencies.

A few days ago, over a hundred upgrades became available, mostly to do with KDE 4.2. I went through the list in aptitude, selecting what to upgrade. I pushed "g" to begin downloading, and it immediately asked for a Gutsy disc. I put the disc in, but the popup text window which asked for the disc did not go away. I tried all of my Gutsy discs, and none of them worked. These are professionally burned dvds, 6 in all, plus a 7th live install dvd. They worked just fine when I installed Gutsy. The only way I could make the popup window go away was to choose the "abort" option. This is the error message I got:

E: Failed to fetch cdrom: [5 of 6]/pool/main/b/boost/libboost-dev_1.34.1-2ubuntu1.1_i386.deb: Disk not found.
E: Unable to correct for unavailable packages

So, even after downloading the hundreds of megabytes of other packages, aptitude did not install any of them, because my chosen install scheme absolutely requires this "libboost" package, which apparently is not available online.

I examined this disc 5 of 6 with Dolphin, and I found the libboost file exactly where aptitude says it looked for it.

One curious point is, Dolphin provides a name for this disc simply "CDROM," nothing indicating Kubuntu or Linux or Gutsy. All 6 of my Gutsy install dvds are labeled "CDROM" by Dolphin. The live install dvd, however, does get a name: Kubuntu 7.10 i386.

Is there some online repository I could add which contains this old package? Any clue would be appreciated.

Thanks for your time!

---

### Post by taurus on 2009-02-27
Look at your /etc/apt/sources.list and make sure you don't have a CDROM as your source.

```
cat /etc/apt/sources.list
```

---

### Post by David J Bush on 2009-02-27
[quote=taurus;6810790]Look at your /etc/apt/sources.list and make sure you don't have a CDROM as your source.

sources.list contains these lines:

deb cdrom:[1 of 6]/ gutsy-updates multiverse universe
deb cdrom:[2 of 6]/ gutsy-updates multiverse universe
deb cdrom:[3 of 6]/ gutsy-updates multiverse universe
deb cdrom:[4 of 6]/ gutsy-updates multiverse universe
deb cdrom:[5 of 6]/ gutsy-updates main
deb cdrom:[6 of 6]/ gutsy-updates main

Is this wrong? I seem to recall it worked when installing Gutsy. If not, what should I change it to?

---

### Post by taurus on 2009-02-27
If you upgraded your machine to intrepid, then those entries for your CDs in /etc/apt/sources.list are not valid anymore.

Therefore, you need to edit /etc/apt/sources.list and place a # in front of those 6 lines to comment them out.

```
kdesu kate /etc/apt/sources.list
```
Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by David J Bush on 2009-02-27
Thanks! I have KDE 4.2 now.

---

