---
title: "How to install old version of package??"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by Dusenberg on 2009-02-11
I recently installed Intrepid 8.10 on my laptop and everything is fine except Kompozer which has a critical bug that means I can't use it to create / update web pages. The version of Kompozer on Gutsy worked and I need to get back to that now as I have a batch of page changes to do ASAP. How do I install an old version of Kompozer as synaptics only shows the latest version?? I've looked on sourceforge and there is an earlier version but its a .gz file and I don't know what to do with it. Any help please?

---

### Post by Partyboi2 on 2009-02-11
You could go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/search?keywords=Kompozer&searchon=names&suite=all&section=all") and manually download the deb package and install by double clicking on it.

---

### Post by Dusenberg on 2009-02-11
> **Partyboi2 said:**
> You could go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/search?keywords=Kompozer&searchon=names&suite=all&section=all") and manually download the deb package and install by double clicking on it.

Many thanks Partyboi2. I tried that but unfortunately this is still the latest version of Kompozer which has the bugs in (0.7.10). I need earlier version of the package any ideas how I can find that?? Much appreciated.

---

### Post by Partyboi2 on 2009-02-11
Go [[COLOR=Blue]here[/COLOR]]("http://kompozer.net/download.php") and download the binary version of kompozer that you want. Once it is downloaded open a terminal (Applications>Accessories>Terminal) and change directory to where the downloaded file is. Eg
```
cd ~/Desktop
```Then extract it with
```
tar xvzf kompozer*.tgz
```
then change into the new directory
```
cd kompozer
```then execute with
```
./kompozer
```

---

### Post by Dusenberg on 2009-02-11
Thanks again Partyboi2 :). I've run out of time now so will try this later.... Cheers!

---

