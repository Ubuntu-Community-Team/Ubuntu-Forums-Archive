---
title: "Help i have a Update problem!!"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by johnnie93 on 2009-09-12
Help me! please read and look at the screensot i took !

everytime i boot up ubuntu it tells me to download some new update and i say oh ok its good to do updates so i click on install updates then........i see this triangle with an "!" in the middle and it tells me that it had lost network connection even though im connected and watching videos on youtube then i tells me that the update package thing is too old! Please Help me!:confused::confused: 

P.S is their a way to download the updates from the teminal????

---

### Post by C0NN3R on 2009-09-12
The message says you have network problems. Shutdown ubuntu and restart your router.

---

### Post by wojox on 2009-09-12
Try:

```
gksudo gedit /etc/apt/sources.list
```

Comment out:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_

---

### Post by Bucky Ball on 2009-09-12
> **wojox said:**
> Try:

```
gksudo gedit /etc/apt/sources.list
```Comment out:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_

+1. That should work. It is left over from the earlier release.

---

### Post by johnnie93 on 2009-09-12
> **wojox said:**
> Try:

```
gksudo gedit /etc/apt/sources.list
```Comment out:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_

what do you mean by comment out # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ ?

i have the newest 9.04

---

### Post by Bucky Ball on 2009-09-12
Just find the line that is the culprit and put '#' in front of it.

---

### Post by 3rag0n on 2009-09-12
It seems that you are using ubuntu 9.04 whereas you have somehow added the 8.10 (old) repository from medibuntu. So, remove this line from your software sources and add the 9.04 repo.
This will do it. :popcorn:

---

### Post by johnnie93 on 2009-09-12
Great nowi have a new error... :(

---

### Post by Bucky Ball on 2009-09-12
You might want to reinstall the Medibuntu repos for Jaunty rather than Intrepid. This seems to be your problem. You also have the old key in there for Intrepid. Delete it.

---

### Post by wojox on 2009-09-12
In the Terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by johnnie93 on 2009-09-12
> **wojox said:**
> In the Terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``````
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

thank you all for your help i really am loving this community :D :popcorn:

---

