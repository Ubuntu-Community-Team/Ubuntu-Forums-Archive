---
title: "How to install Kubuntu on a Ubuntu system?"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by tmcarson1 on 2009-02-04
I wanted to try out the new KDE 4 Kubuntu, and I am able to locate the
kubuntu-desktop in synaptic but when I search for kubuntu-kde4-desktop nothing comes up.

I found a tutorial website here, but it said to install kubuntu-kde4-desktop

Any thoughts are appreciated.

---

### Post by logos34 on 2009-02-04
do u have the 'universe' repository enabled?

---

### Post by tmcarson1 on 2009-02-04
> **logos34 said:**
> do u have the 'universe' repository enabled?


Yes, universe is checked as enabled.  Below are more details:


Ok, under the Ubuntu Software tab I have checked:
(main)
(universe)
(restricted)
(multiverse)

On Third-Party software I have:
archive.canonical.com/ubuntu intrepid
archive.canonical.com/ubuntu intredpid (source code)
ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid (main)
packages.medibuntu.org/intrepid free non-free
pacakges.medibuntu.org/intrepid free non-free (source code)


Now, in synaptic there is a listing for kubuntu-desktop but not one that specifies KDE4.

Any suggestions?
Thanks

---

### Post by taurus on 2009-02-04
Which release are you running?

```
lsb_release -a
```

---

### Post by abn91c on 2009-02-04
```
sudo apt-get install kubuntu-desktop
```

---

### Post by logos34 on 2009-02-04
> **abn91c said:**
> ```
sudo apt-get install kubuntu-desktop
```

abn91c is right--kubuntu-desktop in intrepid is now built around kde4

---

### Post by tmcarson1 on 2009-02-04
> **logos34 said:**
> abn91c is right--kubuntu-desktop in intrepid is now built around kde4

Excellent!  Thanks so much for the help, going to install it now. =)

---

