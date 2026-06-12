---
title: "raid on ati chipset"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by jznomoney on 2009-04-23
Has anyone successfully got a bios raid setup to work and an amd chipset raid?  I have a 780g north bridge and a sb700 south bridge.   I want to install ubuntu 9.04 with a dual boot vista.  I just want to know if anyone has had any success.

---

### Post by jznomoney on 2009-05-26
bump

---

### Post by ronparent on 2009-05-27
I don't see amd listed as a dmraid supported bios (dmraid). If it is actually an amd raid, unless they provide linux raid drivers you probably won't be able to use a 'fakeraid' setup in a dual boot situation with windows. 

You could test it with no actual changes to you system with an ubuntu live cd. Boot from the live cd and open a terminal session (**Applications>Accesoris>Terminal**). Then type in **sudo apt-get install dmraid -**y. If dmraid is successfully installed follow that by **sudo dmraid -r**. This will tell you if dmraid can discover your raid array on your system. If there is output from this last command then you can do it. But read the following before you try: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto). If not then forget it or install ubumtu to its own separate drive (probably a safer option anyway). Good luck.

---

