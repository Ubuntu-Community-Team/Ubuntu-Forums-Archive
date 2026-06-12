---
title: "Google earth FREEZING"
date: 2008-08-10
forum: General Help
---

### Post by qbox on 2008-08-10
Hi
I download and install Google Earth from google-earth web site. I install .bin file. It worked fine until now. When I start the program it work around 2-3 minutes. After that its stop to refresh the images, and when I close the program its is still active and I must kill the ./googleearth process. I can move around the globe but i cant zoom anything.
Any help or to throw this laptop to the garbage including ubuntu 8.04 on it?:mad:

---

### Post by silkstone on 2008-08-10
Is there some reason why you didn't install Google Earth from the repositories with Synaptic?

You must first enable the Medibuntu repos...

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

I've installed GE on a desktop PC and a laptop by this method, and both work fine.

Some people have had a problem with GE and compiz, which can be solved either by turning off desktop effects or unchecking the 'Terrain' option in GE.

---

### Post by qbox on 2008-08-12
Google worked on the first time. Now he freezing.

---

### Post by qbox on 2008-08-14
It fixed by him self :confused::lolflag::)

---

