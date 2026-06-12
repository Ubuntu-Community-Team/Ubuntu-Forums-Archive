---
title: "Flash Player Problems"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by AverellTorrent on 2009-03-15
I have Ubuntu 6.06.1 LTS and I can't seem to get flash player installed right.  Can anybody help?  All the guides I can find are usually for intrepid or something, and I'm having trouble adapting them to work with Dapper.

---

### Post by zvacet on 2009-03-15
You have flashplugin-nonfree in synaptic but you must have** universe** repo enabled.If you don´t know how to do it [here]("https://help.ubuntu.com/community/Repositories/Ubuntu/Dapper") is explanation.Other solution is to add partner repo on your source list and you will do that with 

```
gksudo gedit /etc/apt/sources.list
```

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper partner

Save and close file.

```
sudo apt-get update
```

Then in synaptic try to find adobe-flashplugin

---

